FROM bitnami/oraclelinux-extras:7-r87
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages bzip2-libs glibc keyutils-libs krb5-libs libcom_err libgcc libpcap libselinux libstdc++ ncurses-libs nss-softokn-freebl openssl-libs pcre readline sqlite zlib
RUN bitnami-pkg install node-8.11.4-0 --checksum af7a50f918af19b1e8d530394c151101bb10281877f100f391b50cdcebdb7455
RUN bitnami-pkg install mongodb-client-3.7.9-0 --checksum 7fbdfb5064e75d6b1aebb7a25e272649f20ac267347c8e6cd75e4c555c5ba509
RUN bitnami-pkg unpack parse-3.0.0-0 --checksum 239df8fa5b45058019d93ec599b1548d7560b19da565bb53f975e49c4ad3d9b3

COPY rootfs /
ENV BITNAMI_APP_NAME="parse" \
    BITNAMI_IMAGE_VERSION="3.0.0-ol-7-r1" \
    MONGODB_HOST="mongodb" \
    MONGODB_PASSWORD="" \
    MONGODB_PORT_NUMBER="27017" \
    MONGODB_USER="root" \
    PARSE_APP_ID="myappID" \
    PARSE_HOST="127.0.0.1" \
    PARSE_MASTER_KEY="mymasterKey" \
    PARSE_MOUNT_PATH="/parse" \
    PARSE_PORT_NUMBER="1337" \
    PATH="/opt/bitnami/node/bin:/opt/bitnami/mongodb/bin:/opt/bitnami/parse/bin:$PATH"

EXPOSE 1337

ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "nami", "start", "--foreground", "parse" ]
