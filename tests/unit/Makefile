CFLAGS:=$(CFLAGS)
CC_OBJECTS:=$(CC_OBJECTS)
LIBRMUTIL=../../src/rmutil/librmutil.a
LIBTRIEMAP=../../src/util/triemap/libtriemap.a
LIBGRAPHBLAS = /usr/local/lib/libgraphblas.a

LIBS=$(LIBTRIEMAP) $(LIBRMUTIL)
DEPS=$(CC_OBJECTS) $(LIBS)

SRCDIR := $(shell pwd)
LDFLAGS :=  -lc -lm -ldl -lpthread

CC=gcc
.SUFFIXES: .c .so .xo .o

graph: test_graph.o
	$(CC) $(CFLAGS) -o test_graph test_graph.o  $(DEPS) $(LDFLAGS) -lgraphblas

algebraic_expression: test_algebraic_expression.o
	$(CC) $(CFLAGS) -o test_algebraic_expression test_algebraic_expression.o  $(DEPS) $(LDFLAGS) -lgraphblas

tuples_iter: test_tuples_iter.o
	$(CC) $(CFLAGS) -o test_tuples_iter test_tuples_iter.o  $(DEPS) $(LDFLAGS) -lgraphblas

filter_tree: test_filter_tree.o
	$(CC) $(CFLAGS) -o test_filter_tree test_filter_tree.o  $(DEPS) $(LDFLAGS) -lgraphblas

build: graph algebraic_expression tuples_iter filter_tree

test_graph:
	@(sh -c ./test_graph)
.PHONY: test_graph

test_algebraic_expression:
	@(sh -c ./test_algebraic_expression)
.PHONY: test_algebraic_expression

test_tuples_iter:
	@(sh -c ./test_tuples_iter)
.PHONY: test_tuples_iter

test_filter_tree:
	@(sh -c ./test_filter_tree)
.PHONY: test_filter_tree

test: test_graph test_algebraic_expression test_tuples_iter test_filter_tree

all: build test