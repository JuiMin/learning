
# Get all the C++ source code files in this project
CC_FILES = $(shell find . -name "*.cc")
CC_COMPILED = $(patsubst %.cc, %.o, $(CC_FILES))
# Compiler
CC = g++
# TARGET
TARGET = firstProgram


PHONY: .compiled
.compiled: $(CC_FILES)
	@echo "Compiling C++ file: $?"
	$(CC) -c $? -o $(patsubst %.cc, %.o, $?)
	touch $@

PHONY: .linked
.linked: $(CC_COMPILED)
	mkdir -p install
	$(CC) -o install/$(TARGET) $?
	touch $@

PHONY: install
install: .compiled .linked

PHONY: clean
clean:
	rm -rf install
	$(shell find . -name .compiled -exec rm '{}' \;)
	$(shell find . -name .linked -exec rm '{}' \;)
	$(shell find . -name "*.o" -exec rm '{}' \;)
