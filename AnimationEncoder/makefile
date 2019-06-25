# Copyright (c) 2013- Albert "Alberth" Hofkamp
#
# Permission is hereby granted, free of charge, to any person obtaining a copy of
# this software and associated documentation files (the "Software"), to deal in
# the Software without restriction, including without limitation the rights to
# use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
# of the Software, and to permit persons to whom the Software is furnished to do
# so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in all
# copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
SHELL := /bin/sh

# Assume the user has specified the standard, or c89
override CXXFLAGS += -Wall

ifeq ($(shell uname -s),Darwin) # macOS
	# Bundled, un-updated bison introduce registers which cause non-repo code warnings
	override CXXFLAGS += -Wno-deprecated-register
endif

all:   ## Make the Animation Encoder
	bison --defines=tokens.h --output=parser.cpp parser.y
	flex --outfile=scanner.cpp scanner.l

	$(CXX) $(CXXFLAGS) -c -o ast.o ast.cpp
	$(CXX) $(CXXFLAGS) -c -o parser.o parser.cpp
	$(CXX) $(CXXFLAGS) -c -o scanner.o scanner.cpp
	$(CXX) $(CXXFLAGS) -c -o main.o main.cpp
	$(CXX) $(CXXFLAGS) -c -o image.o image.cpp
	$(CXX) $(CXXFLAGS) -c -o storage.o storage.cpp
	$(CXX) $(CXXFLAGS) -o encoder parser.o scanner.o main.o ast.o image.o storage.o -lpng

clean: ## Remove generated files
	$(RM) encoder parser.o scanner.o main.o ast.o image.o storage.o docs

docs:  ## Create documentation
	doxygen doxy.cfg && echo "Output in doc/html/index.html"

help:  ## Display this help
	@awk 'BEGIN {FS = ":.*##"; printf "Usage:\n  make \033[36m<target>\033[0m\n\nTargets:\n"} \
	  /^[a-zA-Z_-]+:.*?##/ { printf "  \033[36m%-10s\033[0m %s\n", $$1, $$2 }' $(MAKEFILE_LIST)

test: encoder ## Run the encoder on plant animations
	cd ..; AnimationEncoder/encoder plant_anim.txt /dev/null && echo "Success" || echo "-- Problem in input"

.PHONY: all clean docs help test
.DELETE_ON_ERROR:
