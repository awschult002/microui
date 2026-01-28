# Install
TARGET = demo

# Flags
CFLAGS += -I../../src -std=c11 -Wall -Wextra -pedantic -DSDL_DISABLE_IMMINTRIN_H

SRC = main.c ../../src/microui.c renderer.c
OBJ = $(SRC:.c=.o)

ifeq ($(OS),Windows_NT)
TARGET := $(TARGET).exe
LIBS = -lmingw32 -lSDL2main -lSDL2 -lopengl32 -lm -lGLU32
else
	UNAME_S := $(shell uname -s)
	ifeq ($(UNAME_S),Darwin)
		LIBS = -lSDL2 -framework OpenGL -lm
	else
		LIBS = -lSDL2 -lGL -lm -lGLU
	endif
endif

run:
	exec ./$(TARGET)


$(TARGET):
	$(CC) $(SRC) $(CFLAGS) -o $@ $(LIBS)


.PHONY: clean run

clean:
	rm *.o $(TARGET)
