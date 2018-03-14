# use node 9
FROM mhart/alpine-node

WORKDIR /opt/shinobi

# Install package dependencies
RUN apk add --update --no-cache ffmpeg python pkgconfig make g++ git ttf-freefont sqlite socat

# Clone the Shinobi CCTV PRO repo
RUN git clone -b dev https://github.com/ShinobiCCTV/Shinobi.git /opt/shinobi/.

#create entrypoint file
COPY docker-entrypoint.sh .
RUN chmod -f +x ./*.sh

# Install NodeJS dependencies
RUN npm i -g npm@5.6.0
RUN npm install
    
VOLUME ["/opt/shinobi/videos"]
VOLUME ["/opt/dbdata"]

EXPOSE 8080
ENTRYPOINT ["/opt/shinobi/docker-entrypoint.sh" ]
