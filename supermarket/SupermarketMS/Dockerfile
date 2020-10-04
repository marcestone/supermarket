#include <opencv2/core.hpp>
#include <opencv2/imgcodecs.hpp>
#include <opencv2/highgui.hpp>
#include <iostream>
#include <math.h>       /* floor */
using namespace cv;

void nearest_neighbor(img,int w1,int h1,int w2,int h2) {
    int temp [w2*h2];
    double x_ratio = w1/w2 ;
    double y_ratio = h1/h2 ;
    double px, py ; 
    for (int i=0;i<h2;i++) {
        for (int j=0;j<w2;j++) {
            px = floor(j*x_ratio) ;
            py = floor(i*y_ratio) ;
            temp[(i*w2)+j] = img[((py*w1)+px)] ;
        }
    }
    return temp ;
}



int main()
{
    std::string image_path = samples::findFile("opencv_testimage.png");
    Mat img = imread(image_path, IMREAD_COLOR);
    if(img.empty())
    {
        std::cout << "Could not read the image: " << image_path << std::endl;
        return 1;
    }
    imshow("Display window", img);

    img2 = resizePixels(img,2560,1440,720, 480);

    imshow("Display window", img2);

    
    return 0;
}




FROM python:3

ENV PYTHONUNBUFFERED 1
RUN mkdir /code
WORKDIR /code
COPY requirements.txt /code/
RUN pip install -r requirements.txt
COPY . /code/
ARG URL=0.0.0.0:4000

CMD ["sh", "-c", "python manage.py makemigrations supermarket_ms && python manage.py migrate && python manage.py runserver $URL"]