FROM registry.access.redhat.com/ubi9/ubi

ENV PGDATA=/var/lib/pgsql/data

# Install PostgreSQL 13
RUN dnf install -y postgresql-server && \
    dnf clean all

# Create data directory and set permissions
RUN mkdir -p ${PGDATA} && \
    chown -R postgres:postgres ${PGDATA}

# Switch to postgres user (already exists)
USER postgres

# Initialize database
RUN /usr/bin/initdb --pgdata=${PGDATA}

# Expose PostgreSQL port
EXPOSE 5432

# Start PostgreSQL
CMD ["/usr/bin/postgres", "-D", "/var/lib/pgsql/data"]

