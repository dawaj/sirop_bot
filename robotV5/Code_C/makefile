

# options de compilation
CC = gcc
CCFLAGS = -Wall $(INCDIRS) $(LIBSDIR)
LIBSDIR = -L../lib 
LIBS = -lm -lSDL2-2.0 -lSDL2_ttf-2.0 -lSDL2_image-2.0 -lSDL2_gfx
INCDIRS = -I../include


# fichiers du projet
SRC = main.c simu.c wall.c graphique.c semaphore.c 
SRC2 = robot.c client.c
SRC3 = serveur.c semaphore.c
OBJ = $(SRC:.c=.o)
OBJ2 = $(SRC2:.c=.o)
OBJ3 = $(SRC3:.c=.o)
EXEC =simu.out
EXEC2 =robot.out
EXEC3 =serveur.out


# règle initiale
all: $(EXEC) $(EXEC2) $(EXEC3)


# dépendance des .h

wall.o : wall.h wall.c config.h
graphique.o : graphique.c graphique.h config.h robot_api.h
semaphore.o : semaphore.c semaphore.h config.h robot_api.h
simu.o : simu.c simu.h wall.h graphique.h config.h robot_api.h
serveur.o : serveur.c serveur.h semaphore.h config.h robot_api.h
client.o : client.c client.h config.h robot_api.h
main.o: main.c semaphore.h config.h robot_api.h wall.h simu.h graphique.h

# règles de compilation
%.o: %.c
	$(CC) $(CCFLAGS) -o $@ -c $<
	
# règles d'édition de liens
$(EXEC):  $(OBJ)
	$(CC) -o $@ $^ $(LIBS) $(LIBSDIR) 

$(EXEC2): $(OBJ2)
	$(CC) -o $@ $^ $(LIBS) $(LIBSDIR) 

$(EXEC3): $(OBJ3)
	$(CC) -o $@ $^ $(LIBS) $(LIBSDIR) 

# règles supplémentaires
clean:
	rm -rf $(SRC:.c=.o) $(SRC2:.c=.o) $(SRC3:.c=.o)
mproper:
	rm -rf $(EXEC) $(EXEC2) $(EXEC3) $(SRC:.c=.o) $(SRC2:.c=.o) $(SRC3:.c=.o) serveur.log


