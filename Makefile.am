-include $(top_srcdir)/build/modmake.rulesam
AUTOMAKE_OPTIONS = foreign subdir-objects
MODNAME=mod_ssml

LIBS := $(if $(switch_builddir),$(switch_builddir)/libfreeswitch.la,)

IKS_DIR=iksemel
IKS_BUILDDIR=iksemel
IKS_LA=$(IKS_BUILDDIR)/src/libiksemel.la

mod_LTLIBRARIES = mod_ssml.la
mod_ssml_la_SOURCES  = mod_ssml.c
mod_ssml_la_CFLAGS   = $(AM_CFLAGS) $(FREESWITCH_CFLAGS) -I$(IKS_DIR)/include
mod_ssml_la_LIBADD   = $(LIBS) $(IKS_LA)
mod_ssml_la_LDFLAGS  = -avoid-version -module -no-undefined -shared $(FREESWITCH_LIBS)

BUILT_SOURCES=$(IKS_LA)

$(IKS_LA): $(IKS_BUILDDIR) $(IKS_DIR) $(IKS_DIR)/.update
	@cd $(IKS_DIR) && $(MAKE)
	@$(TOUCH_TARGET)

deps: $(IKS_LA)
