include ../Makefile.common

all: compilejava compilec

compilec:
	cc -g -shared -fpic -I${JAVA_HOME}/include -I${JAVA_HOME}/include/$(ARCH) c/recipeNo015_SigSegv.c -o lib/libSigSegv.$(EXT)

compilejava:
	$(JAVA_HOME)/bin/javac -h c -d target java/recipeNo015/SigSegv.java
	$(JAVA_HOME)/bin/javac -h c -d target java/recipeNo015/SigSegvNoHandler.java

test:
	$(JAVA_HOME)/bin/java -Djava.library.path=$(LD_LIBRARY_PATH):./lib -cp target recipeNo015.SigSegv
	$(JAVA_HOME)/bin/java -Djava.library.path=$(LD_LIBRARY_PATH):./lib -cp target recipeNo015.SigSegvNoHandler

clean: clean-common
	$(call rm-test,c/recipeNo015_SigSegv.h)
	$(call rm-test,c/recipeNo015_SigSegvNoHandler.h)
	$(call rm-test,"hs_err*")

include ../Makefile.clean
