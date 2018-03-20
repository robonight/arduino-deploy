FROM dockcross/base:latest

RUN mkdir -p /arduino/setup && mkdir -p /arduino/project
WORKDIR "/arduino/setup"
RUN curl https://downloads.arduino.cc/arduino-1.6.3-linux64.tar.xz -o arduino-1.6.3-linux64.tar.xz
#COPY arduino-1.6.3-linux64.tar.xz arduino-1.6.3-linux64.tar.xz
RUN tar -xvf arduino-1.6.3-linux64.tar.xz  -C /opt
ENV CMAKE_MAKE_PROGRAM=/usr/bin/make

WORKDIR "/arduino"
RUN git clone https://github.com/altexdim/arduino-cmake.git project
RUN rm -rf /arduino/project/example*
RUN sed -i 's/add_subdirectory(example)/add_subdirectory(src)/g' /arduino/project/CMakeLists.txt

VOLUME [ "/arduino/project/src" ]

RUN touch touch.txt 
# change only behind this point
COPY "run.sh" /arduino
ENTRYPOINT [ "./run.sh" ]