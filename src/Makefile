# location of the Python header files
 
PYTHON_VERSION = 2.7
PYTHON_INC = $(shell python-config --includes)
 
DEPENDENCIES = /home/gabriel/cvpr2014/bin/dependencies
# location of the Boost Python include files and library
BOOST_INC = -I/usr/include
BOOST_LIB = -L/usr/local/lib 
FFMPEG_LIB = -L$(DEPENDENCIES)/lib

PYTHON_LIBS = -lboost_python -lpython2.7
OPENCV_LIBS = -lopencv_imgproc -lopencv_core 
FFMPEG_LIBS = -lswscale -lavdevice -lavformat -lavcodec -lswresample -lavutil  
REQUIRED_LIBS = -lpthread -lz -lc -llzma
FFMPEG_INC = -I $(DEPENDENCIES)/include

# compile
TARGET = mpegflow
SOURCE = main
 
$(TARGET).so: $(TARGET).o
	g++ -shared -Wall $(TARGET).o $(BOOST_LIB) $(FFMPEG_LIB) $(OPENCV_LIBS) $(FFMPEG_LIBS) $(REQUIRED_LIBS) $(PYTHON_LIBS)  -o $(TARGET).so
 
$(TARGET).o: $(SOURCE).cpp
	g++ -o $(TARGET).o $(PYTHON_INC) $(BOOST_INC) $(FFMPEG_INC) -fPIC -c $(SOURCE).cpp
.PHONY: clean
clean:
	rm -f $(TARGET).so $(TARGET).o
