NAME = s21_cat
CC = gcc -Wall -Werror -Wextra -std=c11
SOURSES = s21_cat.c
OBJECT = s21_cat.o
LIB = s21_cat.h

all: clean s21_cat

$(NAME): $(OBJECT)
	$(CC) $(OBJECT) -o $(NAME)

s21_cat.o: s21_cat.c
	$(CC) $(SOURSES) $(LIB) -c

rebuild:
	$(MAKE) clean
	$(MAKE) all

clean: 
	rm -rf *.o *.gch *.out log.txt s21_cat

check: s21_cat
	cppcheck --enable=all --suppress=missingIncludeSystem . *.c *.h
	cp ../../materials/linters/CPPLINT.cfg ./
	python3 ./../../materials/linters/cpplint.py --extensions=c *.c *.h
	rm -f CPPLINT.cfgd
	leaks --atExit -- ./s21_cat 

test: t_cat.sh
	bash t_cat.sh
