#include "inttypes.h"
#include "stdarg.h"
#include "include/console.h"
#include "include/tasks.h"

void setpixel(int x, int y, unsigned char color) {
unsigned char* VGA = (unsigned char*) 0xA0000;
  int offset;
  if(0 <= x && x < 320) {
    if(0 <= y && y < 200) {
      offset = 320*y + x;
      VGA[offset] = color;
    }
  }
}
 
static inline void outb(uint16_t port, uint8_t data)
{
    asm volatile ("outb %0, %1" : : "a" (data), "Nd" (port));
}
void printchar(uint8_t chr, uint8_t color, uint8_t x, uint8_t y)
{
  uint16_t* off = (uint16_t*)0xB8000;
  // berechnen der Adresse
  off += y * 80 + x;  // eine Multiplikation mit 2 darf hier nicht erfolgen, da off vom type uint16_t ist
  // setzen des zeichens + attributebyte
  *off = (((uint16_t)color) << 8) | chr;
}

void println(const char* s, uint8_t color, uint8_t y)
{

}

void printo(const char hw[], int color) {

    int i;
    char* video = (char*) 0xb8000;
    // C-Strings haben ein Nullbyte als Abschluss
    for (i = 0; hw[i] != '\0'; i++) {
 
        // Zeichen i in den Videospeicher kopieren
        video[i * 2] = hw[i];

        // 0x07 = Hellgrau auf Schwarz
        video[i * 2 + 1] = 0x07;

video[i * 2 + 1] = (char*) color;
    }

}
void clear(void) {

    int i;
    char* hw = "                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  ";
    char* video = (char*) 0xb8000;
    // C-Strings haben ein Nullbyte als Abschluss
    for (i = 0; hw[i] != '\0'; i++) {
 
        // Zeichen i in den Videospeicher kopieren
        video[i * 2] = hw[i];

        // 0x07 = Hellgrau auf Schwarz
        video[i * 2 + 1] = 0x07;
    }

}

 
void init(void)
{
/* Clear the screen */

clear();
kprintf(" NamelessOS(0.0.1 prealpha)\n");
}
