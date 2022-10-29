FROM node:16.18.0-alpine
EXPOSE 4321 35729
ENV NPM_CONFIG_PREFIX=/usr/app/.npm-global \
  PATH=$PATH:/usr/app/.npm-global/bin
VOLUME /usr/app/spfx
WORKDIR /usr/app/spfx
RUN useradd --create-home --shell /bin/bash spfx 
RUN usermod -aG sudo spfx
RUN chown -R spfx:spfx /usr/app
USER spfx
RUN npm i -g gulp-cli
RUN npm i -g yo
RUN npm i -g @microsoft/generator-sharepoint
CMD /bin/bash