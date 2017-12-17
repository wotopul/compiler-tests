TESTS=test001 test002

.PHONY: check $(TESTS) 

check: $(TESTS) 

$(TESTS): %: %.expr
	RC_RUNTIME=../../runtime ../../rc -om $<
	cat $@.input | MALLOC_TRACE=./mtrace-$@.log ./$@ > $@.log
	diff $@.log orig/$@.log
	mtrace ./$@ ./mtrace-$@.log

clean:
	rm -f test*.log mtrace*.log *.s *~ $(TESTS)
