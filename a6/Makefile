###
# This Makefile can be used to make a parser for the CSX language
# (parser.class) and to make a program (P4.class) that tests the parser and
# the unparse methods in ast.java.
#
# make clean removes all generated files.
#
###

JC = javac -classpath .:java_cup.jar:JLex.jar
J = java -classpath .:java_cup.jar:JLex.jar

P6.class: P6.java Codegen.class parser.class Yylex.class ASTnode.class Registers.class
	$(JC) -g P6.java

parser.class: parser.java ASTnode.class Yylex.class ErrMsg.class
	$(JC) parser.java

parser.java: CSX.cup
	$(J) java_cup.Main < CSX.cup

Yylex.class: CSX.jlex.java sym.class ErrMsg.class
	$(JC) CSX.jlex.java

ASTnode.class: ast.java
	$(JC) -g ast.java

Codegen.class: Codegen.java
	$(JC) -g Codegen.java

Registers.class: Registers.java
	$(JC) -g Registers.java

CSX.jlex.java: CSX.jlex sym.class
	$(J) JLex.Main CSX.jlex

sym.class: sym.java
	$(JC) -g sym.java

sym.java: CSX.cup
	$(J) java_cup.Main < CSX.cup

SymTable.class: SymTable.java
	$(JC) SymTable.java

Sym.class: Sym.java
	$(JC) -g Sym.java

ErrMsg.class: ErrMsg.java
	$(JC) ErrMsg.java

###
# clean
###
clean:
	rm -f *~ *.class parser.java CSX.jlex.java sym.java
