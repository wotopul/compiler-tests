TESTS=test001 test002 test003 test004 test005 core028 core029 core030a core030b core030

.PHONY: check $(TESTS) 

check: $(TESTS) 

$(TESTS): %: %.expr
	RC_RUNTIME=../../runtime ../../rc -om $<
	cat $@.input | MALLOC_TRACE=./mtrace-$@.log ./$@ > $@.log
	diff $@.log orig/$@.log
	mtrace ./$@ ./mtrace-$@.log

clean:
	rm -f *.log *.s *~ $(TESTS)
