################################################################################
#
# Copyright (c) 2011, EURid. All rights reserved.
# The YADIFA TM software product is provided under the BSD 3-clause license:
#
# Redistribution and use in source and binary forms, with or without 
# modification, are permitted provided that the following conditions
# are met:
#
#        * Redistributions of source code must retain the above copyright 
#          notice, this list of conditions and the following disclaimer.
#        * Redistributions in binary form must reproduce the above copyright 
#          notice, this list of conditions and the following disclaimer in the 
#          documentation and/or other materials provided with the distribution.
#        * Neither the name of EURid nor the names of its contributors may be 
#          used to endorse or promote products derived from this software 
#          without specific prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
# AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE 
# IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
# DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE 
# FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL 
# DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR 
# SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
# CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
# OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
# OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
#
################################################################################
#
#	YADIFA config Makefile.am script
#
#      	Makefile.am script
#
#	$URL: https://svn.int.eurid.eu/svn/sysdevel/projects/yadifa/tags/release-2.1.2-public/etc/Makefile.am $
#
#	$Date: 2014-12-11 11:24:53 +0100 (Don, 11 Dez 2014) $
#
#	$Revision: 4563 $
#
##############################################################################

ACLOCAL_AMFLAGS = -I m4

OC=yadifad.conf
OCE=$(OC).example
YI=yadifad.init
YIE=$(YI).example

doc_DATA = $(OCE) $(YIE) yadifad-master.conf.example yadifad-slave.conf.example \
				yadifad.init.debian	yadifad.init.rhel \
				yadifad.logrotate \
				yadifad.service yadifad.service.arch yadifad.service.debian yadifad.service.rhel

noinst_HEADERS = yadifad.conf.example yadifad-master.conf.example yadifad-slave.conf.example \
				yadifad.init.example yadifad.init.debian yadifad.init.rhel \
				yadifad.logrotate \
				yadifad.service yadifad.service.arch yadifad.service.debian yadifad.service.rhel \
				$(OC) $(YI)

$(OC): $(OCE)
	cat $(OCE) | sed "s@\"\(.*\)/var/\(.*\)\"@\"$(localstatedir)/\2\"@" > $(OC)

$(YI): $(YIE)
	cat $(YIE) | sed "s@^PREFIX=.*@PREFIX=\"$(prefix)\"@" > $(YI)

all: $(YI) $(OC)

install-data-hook: $(OC)
	mkdir -p $(DESTDIR)$(sysconfdir)
	touch $(DESTDIR)$(sysconfdir)/$(OC)

clean-local:
	rm -f $(YI) $(OC)

release: $(YI) $(OC)

profile: $(YI) $(OC)

debug: $(YI) $(OC)
