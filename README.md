# hello-world
just another repository
#include "opencv2/core/core.hpp"  
#include "opencv2/highgui/highgui.hpp"  
#include "opencv2/imgproc/imgproc.hpp"  
#include <iostream>  
using namespace cv;
using namespace std;

void processiamge(Mat &frame)
{
	circle(frame, Point(cvRound(frame.cols / 2), cvRound(frame.rows / 2)), 150, Scalar(0, 0, 255), 2, 8);
}

int main()
{
	string filename = "D:\\study materials\\video\\Video 14.mp4";//打开的视频文件  
	VideoCapture capture;
	capture.open(filename);

	double rate = capture.get(CV_CAP_PROP_FPS);//获取视频文件的帧率  
	int delay = cvRound(1000.000 / rate);

	if (!capture.isOpened())//判断是否打开视频文件  
	{
		return -1;
	}

	else
	{
		while (true)
		{
			Mat frame;
			capture >> frame;//读出每一帧的图像  
			if (frame.empty()) break;
			imshow("处理前视频", frame);
			processiamge(frame);
			imshow("处理后视频", frame);
			waitKey(delay);
		}
	}
	return 0;
}
