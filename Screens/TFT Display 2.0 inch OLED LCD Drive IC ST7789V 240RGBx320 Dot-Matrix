#include <Adafruit_GFX.h>
#include <Adafruit_ST7789.h>
#include <SPI.h>

// ================= TFT PINS =================
#define TFT_CS    5
#define TFT_DC    2
#define TFT_RST   4
#define TFT_MOSI  23
#define TFT_SCLK  18

// ================= DISPLAY =================
Adafruit_ST7789 tft = Adafruit_ST7789(TFT_CS, TFT_DC, TFT_RST);

// ================= TEST VARIABLES =================
unsigned long frameCount = 0;
unsigned long testStartTime = 0;
float angle = 0;
int colorCycle = 0;

void setup() {
  Serial.begin(115200);
  delay(500);
  
  Serial.println("\n\n========== ST7789V EXTREME STRESS TEST ==========");
  Serial.println("Starting maximum performance test...\n");
  
  // ================= START SPI =================
  SPI.begin(TFT_SCLK, -1, TFT_MOSI, TFT_CS);
  
  // ================= INIT DISPLAY =================
  tft.init(240, 320);
  tft.setRotation(1);
  
  Serial.println("Display initialized");
  testStartTime = millis();
  
  // ================= EXTREME TESTS =================
  extremeColorFlood();
  delay(500);
  
  extremePixelBlast();
  delay(500);
  
  extremeShapeStorm();
  delay(500);
  
  extremeLineNoise();
  delay(500);
  
  extremeCircleExplosion();
  delay(500);
  
  extremeGradientShift();
  delay(500);
  
  extremeTextRain();
  delay(500);
  
  extremeFractalZoom();
  delay(500);
  
  extremeWaveAnimation();
  delay(500);
  
  extremeParticleSwarm();
  delay(500);
  
  extremePerformanceBenchmark();
  delay(500);
  
  extremeScreenBurn();
  
  Serial.println("\n========== ALL EXTREME TESTS COMPLETE ==========\n");
}

void loop() {
}

// TEST 1: Rapid color flooding
void extremeColorFlood() {
  Serial.println("TEST 1: Extreme Color Flood");
  unsigned long testTime = millis();
  int floodCount = 0;
  
  while (millis() - testTime < 3000) {
    uint16_t randomColor = tft.color565(random(256), random(256), random(256));
    tft.fillScreen(randomColor);
    floodCount++;
  }
  
  unsigned long elapsed = millis() - testTime;
  Serial.print("  Floods per second: ");
  Serial.println((floodCount * 1000) / elapsed);
}

// TEST 2: Pixel blast - direct pixel writes
void extremePixelBlast() {
  Serial.println("TEST 2: Extreme Pixel Blast");
  tft.fillScreen(ST77XX_BLACK);
  
  unsigned long testTime = millis();
  int pixelCount = 0;
  
  while (millis() - testTime < 2000) {
    for (int i = 0; i < 1000; i++) {
      int x = random(320);
      int y = random(240);
      uint16_t color = tft.color565(random(256), random(256), random(256));
      tft.drawPixel(x, y, color);
      pixelCount++;
    }
  }
  
  unsigned long elapsed = millis() - testTime;
  Serial.print("  Pixels per second: ");
  Serial.println((pixelCount * 1000) / elapsed);
}

// TEST 3: Shape storm - rapid random shapes
void extremeShapeStorm() {
  Serial.println("TEST 3: Extreme Shape Storm");
  tft.fillScreen(ST77XX_BLACK);
  
  unsigned long testTime = millis();
  int shapeCount = 0;
  
  while (millis() - testTime < 2000) {
    int x = random(320);
    int y = random(240);
    int size = random(5, 50);
    uint16_t color = tft.color565(random(256), random(256), random(256));
    
    int shapeType = random(4);
    
    if (shapeType == 0) {
      tft.drawRect(x, y, size, size, color);
    } else if (shapeType == 1) {
      tft.fillRect(x, y, size, size, color);
    } else if (shapeType == 2) {
      tft.drawCircle(x, y, size / 2, color);
    } else {
      tft.fillCircle(x, y, size / 2, color);
    }
    shapeCount++;
  }
  
  unsigned long elapsed = millis() - testTime;
  Serial.print("  Shapes per second: ");
  Serial.println((shapeCount * 1000) / elapsed);
}

// TEST 4: Line noise pattern
void extremeLineNoise() {
  Serial.println("TEST 4: Extreme Line Noise");
  tft.fillScreen(ST77XX_BLACK);
  
  unsigned long testTime = millis();
  int lineCount = 0;
  
  while (millis() - testTime < 2000) {
    int x1 = random(320);
    int y1 = random(240);
    int x2 = random(320);
    int y2 = random(240);
    uint16_t color = tft.color565(random(256), random(256), random(256));
    
    tft.drawLine(x1, y1, x2, y2, color);
    lineCount++;
  }
  
  unsigned long elapsed = millis() - testTime;
  Serial.print("  Lines per second: ");
  Serial.println((lineCount * 1000) / elapsed);
}

// TEST 5: Circle explosion
void extremeCircleExplosion() {
  Serial.println("TEST 5: Extreme Circle Explosion");
  tft.fillScreen(ST77XX_BLACK);
  
  for (int explosion = 0; explosion < 50; explosion++) {
    int centerX = 160;
    int centerY = 120;
    
    for (int radius = 2; radius < 100; radius += 3) {
      uint16_t color = tft.color565(
        (255 * radius) / 100,
        (255 * (100 - radius)) / 100,
        128
      );
      tft.drawCircle(centerX, centerY, radius, color);
    }
  }
  
  Serial.println("  50 circle explosions completed");
}

// TEST 6: Gradient shift animation
void extremeGradientShift() {
  Serial.println("TEST 6: Extreme Gradient Shift");
  
  for (int shift = 0; shift < 100; shift++) {
    for (int x = 0; x < 320; x += 2) {
      uint8_t r = (255 * ((x + shift * 5) % 320)) / 320;
      uint8_t g = (255 * ((x + shift * 3) % 320)) / 320;
      uint8_t b = (255 * ((x + shift * 7) % 320)) / 320;
      uint16_t color = tft.color565(r, g, b);
      
      tft.drawFastVLine(x, 0, 240, color);
    }
  }
  
  Serial.println("  100 gradient frames completed");
}

// TEST 7: Text rain
void extremeTextRain() {
  Serial.println("TEST 7: Extreme Text Rain");
  tft.fillScreen(ST77XX_BLACK);
  
  for (int frame = 0; frame < 60; frame++) {
    for (int i = 0; i < 20; i++) {
      int x = random(300);
      int y = random(240);
      uint16_t color = tft.color565(random(256), random(256), random(256));
      
      tft.setTextColor(color);
      tft.setTextSize(random(1, 3));
      tft.setCursor(x, y);
      tft.print(random(10));
    }
  }
  
  Serial.println("  60 text frames completed");
}

// TEST 8: Fractal-like zoom effect
void extremeFractalZoom() {
  Serial.println("TEST 8: Extreme Fractal Zoom");
  
  for (int zoom = 0; zoom < 50; zoom++) {
    tft.fillScreen(ST77XX_BLACK);
    
    int size = 150 - (zoom * 3);
    int centerX = 160;
    int centerY = 120;
    
    // Draw nested rectangles
    for (int i = 0; i < 20; i++) {
      uint16_t color = tft.color565(
        (i * 12) % 256,
        (i * 7) % 256,
        (i * 15) % 256
      );
      
      int w = size - (i * 4);
      int h = (size / 4) * 3 - (i * 3);
      
      if (w > 0 && h > 0) {
        tft.drawRect(centerX - w / 2, centerY - h / 2, w, h, color);
      }
    }
  }
  
  Serial.println("  50 zoom frames completed");
}

// TEST 9: Wave animation
void extremeWaveAnimation() {
  Serial.println("TEST 9: Extreme Wave Animation");
  
  for (int frame = 0; frame < 40; frame++) {
    tft.fillScreen(ST77XX_BLACK);
    
    for (int x = 0; x < 320; x += 10) {
      int y = 120 + (int)(30 * sin((x + frame * 10) * 3.14159 / 180));
      uint16_t color = tft.color565(
        (frame * 6) % 256,
        (x / 320) * 255,
        150
      );
      
      tft.fillCircle(x, y, 8, color);
    }
  }
  
  Serial.println("  40 wave frames completed");
}

// TEST 10: Particle swarm
void extremeParticleSwarm() {
  Serial.println("TEST 10: Extreme Particle Swarm");
  tft.fillScreen(ST77XX_BLACK);
  
  int particles[100][2];
  int velocities[100][2];
  
  // Initialize particles
  for (int i = 0; i < 100; i++) {
    particles[i][0] = random(320);
    particles[i][1] = random(240);
    velocities[i][0] = random(-3, 4);
    velocities[i][1] = random(-3, 4);
  }
  
  // Animate particles
  for (int frame = 0; frame < 200; frame++) {
    tft.fillScreen(ST77XX_BLACK);
    
    for (int i = 0; i < 100; i++) {
      particles[i][0] += velocities[i][0];
      particles[i][1] += velocities[i][1];
      
      // Wrap around screen
      if (particles[i][0] < 0) particles[i][0] = 320;
      if (particles[i][0] > 320) particles[i][0] = 0;
      if (particles[i][1] < 0) particles[i][1] = 240;
      if (particles[i][1] > 240) particles[i][1] = 0;
      
      uint16_t color = tft.color565(
        (frame + i * 2) % 256,
        (i * 5) % 256,
        (frame * 2) % 256
      );
      
      tft.fillCircle(particles[i][0], particles[i][1], 2, color);
    }
  }
  
  Serial.println("  200 frames x 100 particles completed");
}

// TEST 11: Performance benchmark - maximum throughput
void extremePerformanceBenchmark() {
  Serial.println("TEST 11: Extreme Performance Benchmark");
  
  // Benchmark 1: fillScreen speed
  Serial.println("  Benchmark 1: Full screen fills");
  unsigned long startTime = millis();
  int fillCount = 0;
  
  while (millis() - startTime < 1000) {
    tft.fillScreen(tft.color565(random(256), random(256), random(256)));
    fillCount++;
  }
  Serial.print("    Fills per second: ");
  Serial.println(fillCount);
  
  // Benchmark 2: drawFastHLine speed
  Serial.println("  Benchmark 2: Fast horizontal lines");
  tft.fillScreen(ST77XX_BLACK);
  startTime = millis();
  int hlineCount = 0;
  
  while (millis() - startTime < 1000) {
    for (int y = 0; y < 240; y++) {
      tft.drawFastHLine(0, y, 320, tft.color565(random(256), random(256), random(256)));
      hlineCount++;
    }
  }
  Serial.print("    H-lines per second: ");
  Serial.println(hlineCount);
  
  // Benchmark 3: drawFastVLine speed
  Serial.println("  Benchmark 3: Fast vertical lines");
  tft.fillScreen(ST77XX_BLACK);
  startTime = millis();
  int vlineCount = 0;
  
  while (millis() - startTime < 1000) {
    for (int x = 0; x < 320; x++) {
      tft.drawFastVLine(x, 0, 240, tft.color565(random(256), random(256), random(256)));
      vlineCount++;
    }
  }
  Serial.print("    V-lines per second: ");
  Serial.println(vlineCount);
  
  // Benchmark 4: Random pixels
  Serial.println("  Benchmark 4: Random pixels");
  tft.fillScreen(ST77XX_BLACK);
  startTime = millis();
  int pixCount = 0;
  
  while (millis() - startTime < 1000) {
    for (int i = 0; i < 1000; i++) {
      tft.drawPixel(random(320), random(240), tft.color565(random(256), random(256), random(256)));
      pixCount++;
    }
  }
  Serial.print("    Pixels per second: ");
  Serial.println(pixCount * 1000);
}

// TEST 12: Screen burn-in test (colorful pattern)
void extremeScreenBurn() {
  Serial.println("TEST 12: Extreme Screen Burn (Running 30 sec)");
  
  unsigned long burnStartTime = millis();
  int pattern = 0;
  
  while (millis() - burnStartTime < 30000) {
    // Rotating checkerboard pattern
    for (int y = 0; y < 240; y++) {
      for (int x = 0; x < 320; x++) {
        uint16_t color;
        
        if (((x / 20) + (y / 20) + pattern) % 2 == 0) {
          color = tft.color565(255, 0, 0);    // Red
        } else {
          color = tft.color565(0, 255, 0);    // Green
        }
        
        tft.drawPixel(x, y, color);
      }
    }
    pattern++;
  }
  
  // Final colorful bars
  tft.fillScreen(ST77XX_BLACK);
  int barWidth = 320 / 7;
  
  uint16_t colors[] = {
    ST77XX_RED, ST77XX_YELLOW, ST77XX_GREEN,
    ST77XX_CYAN, ST77XX_BLUE, ST77XX_MAGENTA, ST77XX_WHITE
  };
  
  for (int i = 0; i < 7; i++) {
    tft.fillRect(i * barWidth, 0, barWidth, 240, colors[i]);
  }
  
  Serial.println("  Screen burn test completed");
}
