
compile: *.java *.cs
	javac *.java
	gmcs HelloTest.cs
	gcc -Wall -o hellotest hellotest.c
	6g go-hellotest.go
	6l -o go-hellotest go-hellotest.6

test: test.csv

test.csv: compile
	rm -f $@ test2.csv $@.new
	./runtests python ./hellotest.py >>$@.new
	./runtests jython ./hellotest.py >>$@.new
	./runtests pypy ./hellotest.py >>$@.new
	./runtests java HelloTest >>$@.new
	./runtests java -client HelloTest >>$@.new
	./runtests java -XX:+UseConcMarkSweepGC HelloTest >>$@.new
	./runtests mono HelloTest.exe >>$@.new
	./runtests perl hellotest.pl >>$@.new
	./runtests ruby1.8 ./hellotest.rb >>$@.new
	./runtests ruby1.9 ./hellotest.rb >>$@.new
	./runtests ./hellotest >>$@.new
	./runtests valgrind ./hellotest >>$@.new
	./runtests ./go-hellotest >>$@.new
	
	mv $@.new $@

clean:
	rm -f *~ .*~ *.class *.new *.6 *.exe \
		test*.csv hellotest hellotest2 go-hellotest
