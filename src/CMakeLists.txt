cmake_minimum_required(VERSION 3.5)
project(yolov4_darknet)
#find_package( OpenCV 3 REQUIRED )


#REQUIRED
#set(OpenCV_DIR     ~/installCv3414Ubun2104FullNew/share/OpenCV     )
#set(Opencv_rot_my   ~/cv3414Bundle/installCv3414Ubun2104FullNew  )
set(Opencv_rot_my   ~/installCv3414Ubun2104FullNew  )
set(OpenCV_DIR     ${Opencv_rot_my}/share/OpenCV     )
find_package(   opencv    PATHS    ${Opencv_rot_my}/share/OpenCV    )
include_directories(   ${Opencv_rot_my}/include
    ${Opencv_rot_my}/include/opencv
    ${Opencv_rot_my}/include/opencv2
    )
link_directories( ${Opencv_rot_my}/lib )

link_directories( ../lib  )

set(CMAKE_CXX_STANDARD 14)
include_directories(${OpenCV_INCLUDE_DIRS})
add_executable(yolov4_darknet main.cpp yolo_v2_class.hpp)
target_link_libraries(yolov4_darknet ${OpenCV_LIBS} -L./   libdarknet.so libpthread.so.0

#    PRIVATE Qt${QT_VERSION_MAJOR}::Widgets
#        ${OpenCV_LIBS}
        libopencv_core.so   libopencv_highgui.so  libopencv_imgcodecs.so
        libopencv_imgproc.so   libopencv_videoio.so     libopencv_ml.so
        libopencv_features2d.so  libopencv_flann.so  libopencv_objdetect.so
          libopencv_dnn.so
          libopencv_tracking.so
          libopencv_video.so
          libopencv_videostab.so
          libopencv_xfeatures2d.so
        #    -lpng  -lthread -ljpeg  -lpng16
        #     nlohmann_json::nlohmann_json
        #     tinyxml2::tinyxml2
        #     glog::glog
#        -lhalconcpp -lhalcon -lXext -lX11 -ldl -lpthread
    )


set(EXECUTABLE_OUTPUT_PATH  ../bin )
