opencv中的cadcade train
1. traincascade.cpp
   class :  CvCascadeClassifier
   class :  CvCascadeParams
   class :  CvCascadeBoostParams
   
2....


3.Makefile
OpenCV_INC_PATH = /usr/include/opencv/
OpenCV_LIB_PATH = /usr/lib

VPATH = $(OpenCV_INC_PATH)

#C_ARGS = -fopenmp -Wno-unused-result -O2
C_ARGS = -Wno-unused-result -O2
TARGET = train

CXX = g++
CC = gcc

%.o: %.cpp
	$(CXX) $(C_ARGS) -c $^ -o $@ -I$(OpenCV_INC_PATH)

objects = traincascade.o cascadeclassifier.o boost.o features.o HOGfeatures.o lbpfeatures.o haarfeatures.o imagestorage.o

$(TARGET): $(objects)
	$(CXX) $(C_ARGS) $^ -o $@ -I$(OpenCV_INC_PATH) -L$(OpenCV_LIB_PATH) `pkg-config --cflags --libs opencv`

clean:
	rm -f *.o $(TARGET)
