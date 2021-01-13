Image rotation using OpenCV

Introduction
OpenCV is a library of programming functions mainly aimed at real-time computer vision. Originally developed by Intel, it was later supported by Willow Garage then Itseez. The library is cross-platform and free for use under the open-source Apache 2 License. Starting with 2011, OpenCV features GPU acceleration for real-time operations.
C++ is an Object-Oriented Language using the implementation of the OpenCV libraries to do all the function.
Code used and its description
#include <opencv2/opencv.hpp>
#include <iostream>


using namespace cv;
using namespace std;

Mat rotate(Mat src, double angle)      
{
    Mat dst;      
    Point2f pt(src.cols / 2., src.rows / 2.);          
    Mat r = getRotationMatrix2D(pt, angle, 1.0);      
    warpAffine(src, dst, r, Size(src.cols, src.rows));  
    return dst;         
}

int main()
{
    string str;         
    cout << "Read Image:";      
    cin >> str;     
    double angle;       
    cout << "Enter the angle:";
    cin >> angle;
    Mat src = imread(str,1);           
    
    Mat dst;      
    dst = rotate(src, angle);       

    imshow("src", src);          
    imshow("dst", dst);          
    waitKey(0);                     
    return 0;
}

OpenCV is imported using the #include <opencv2/opencv.hpp>
	The Mat is used to make the object and use different operations on it.
	The imread function is used to read the image with the given format specified.(Original, B/W, Coloured)
	The imshow function is used to display the image on the screen.
	The waitKey is used to hold the image on the screen.
	rotate function is user defined function to rotate the image with the given degree.
	rotate uses the following function-
o	Point2f
	It is the point from where the image is to be rotated
o	getRotationMarix2D
	A 2D matrix for storing the matrix.
o	warpAffine
	To apply an Affine transformation to the image.
 




