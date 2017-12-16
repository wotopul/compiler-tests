TESTS=test001 test002

.PHONY: check $(TESTS) 

check: $(TESTS) 

$(TESTS): %: %.expr
	RC_RUNTIME=../../runtime ../../rc -o $< && cat $@.input | ./$@ > $@.log && diff $@.log orig/$@.log
	cat $@.input | ../../rc -i $< > $@.log && diff $@.log orig/$@.log
	cat $@.input | ../../rc -s $< > $@.log && diff $@.log orig/$@.log

clean:
	rm -f test*.log *.s *~ $(TESTS)
