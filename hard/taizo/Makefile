IGN     = $(patsubst %.bu,%.ign,$(wildcard *.bu))
TARGETS = $(filter taizo%,${IGN})
DEPS    = $(filter-out ${TARGETS},$(IGN))

.PHONY: all clean
all: ${TARGETS}
clean:
	rm -rf *.ign

%.ign: %.bu
	butane -sd. -o $@ $<

${TARGETS}: ${DEPS}
