#
# Copyright (C) 2011-2021 Intel Corporation. All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions
# are met:
#
#   * Redistributions of source code must retain the above copyright
#     notice, this list of conditions and the following disclaimer.
#   * Redistributions in binary form must reproduce the above copyright
#     notice, this list of conditions and the following disclaimer in
#     the documentation and/or other materials provided with the
#     distribution.
#   * Neither the name of Intel Corporation nor the names of its
#     contributors may be used to endorse or promote products derived
#     from this software without specific prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
# "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
# LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
# A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
# OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
# SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
# LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
# DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
# THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
# (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
# OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
#
#

include ../../../buildenv.mk

CPPFLAGS += -I$(COMMON_DIR)/inc          \
            -I$(COMMON_DIR)/inc/internal \
            -DTEST=1 -g

.PHONY: all clean

all: test_bit_array test_ema test_public test_emm

test_bit_array: test_bit_array.c ../bit_array.c
	@$(CC) $(CPPFLAGS) $^ -o $@

test_ema: test_ema.c stub.c ../ema.c ../bit_array.c
	@$(CC) $(CPPFLAGS) $^ -o $@

test_public: test_public.c stub.c ../sgx_mm.c ../ema.c ../bit_array.c
	@$(CC) $(CPPFLAGS) $^ -o $@

test_emm: test_emm.c stub.c ../emm_private.c ../sgx_mm.c ../ema.c ../bit_array.c
	@$(CC) $(CPPFLAGS) $^ -o $@

clean:
	@$(RM) test_bit_array test_ema test_public test_emm
