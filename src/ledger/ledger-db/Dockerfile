# Copyright 2020 Google LLC
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
FROM postgres:16.1-alpine@sha256:a1b267d05ee39210d162185f52645687c7e63fbe25b8c58ccd7f81f0a7e2ad97

# Need to get coreutils to get the date bash function working properly:
RUN apk add --update coreutils && rm -rf /var/cache/apk/*

COPY initdb/0_init_tables.sql /docker-entrypoint-initdb.d/0_init_tables.sql
RUN chmod 755  /docker-entrypoint-initdb.d/0_init_tables.sql

COPY initdb/1_create_transactions.sh /docker-entrypoint-initdb.d/1_create_transactions.sh
RUN chmod 755  /docker-entrypoint-initdb.d/1_create_transactions.sh
