ARG PG_MAJOR=17
ARG PG_VECTOR=0.7.4

FROM postgres:$PG_MAJOR

ARG PG_MAJOR
ARG PG_VECTOR

RUN apt-get update && \
		apt-mark hold locales && \
		apt-get install -y --no-install-recommends git ca-certificates build-essential postgresql-server-dev-$PG_MAJOR && \
    git clone --branch v$PG_VECTOR https://github.com/pgvector/pgvector.git /tmp/pgvector && \
		cd /tmp/pgvector && \
		make clean && \
		make OPTFLAGS="" && \
		make install && \
		mkdir /usr/share/doc/pgvector && \
		cp LICENSE README.md /usr/share/doc/pgvector && \
		rm -r /tmp/pgvector && \
		apt-get remove -y build-essential git ca-certificates postgresql-server-dev-$PG_MAJOR && \
		apt-get autoremove -y && \
		apt-mark unhold locales && \
		rm -rf /var/lib/apt/lists/*
