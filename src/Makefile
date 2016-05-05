LIBNAME:=uutf
VERSION:=0.9.4
DESCRIPTION:=Non-blocking streaming Unicode codec for OCaml
REQUIRES:=cmdliner
OPT:=ocamlfind ocamlopt -g
OPT:=ocamlfind ocamlopt -g
OCAMLC:=ocamlfind ocamlc -g 
LIBSRC:=\
	uutf.mli uutf.ml

all: uutf.cma uutf.cmxa

uutf.cma: uutf.mli uutf.ml
	$(OCAMLC) -package $(REQUIRES) -o $@ -a $(LIBSRC)

uutf.cmxa: uutf.mli uutf.ml
	$(OPT) -package $(REQUIRES) -o $@ -a $(LIBSRC)

META: Makefile
	echo "description = \"$(DESCRIPTION)\"" > $@
	echo "version = \"$(VERSION)\"" >> $@
	echo "archive(byte) = \"$(LIBNAME).cma\"" >> $@
	echo "archive(native) = \"$(LIBNAME).cmxa\"" >> $@
	echo "requires = \"$(REQUIRES)\"" >> $@

install:
	ocamlfind install $(LIBNAME) *.a *.cm[ioxa] *.cmx[as] uutf.mli META

uninstall:
	ocamlfind remove $(LIBNAME)

reinstall:
	make uninstall
	make install

clean:
	rm -f *.cmi *.cmo *.cmx *.cma *.a *.cmxa *.o

rebuild:
	make clean
	make all
