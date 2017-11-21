#!/bin/bash
if [ "$1" = "-h" -o "$1" = "--help" ];then
echo "This program take your jpg picture"
echo "And make gif animation"
echo "$0 [angle] [animation duration in 1/100 second] [.jpg image's name without \".jpg\"] [GIF file's name without \".jpg\"]"
exit 0;
fi
if ! [[ $1 =~ ^[0-9]+$ ]] ; then
echo "enter the tilt angle"
exit 0;
fi
if ! [[ $2 =~ ^[0-9]+$ ]] ; then
echo "enter the duration of the animation"
exit 0;
fi
if [ "$3" = "" ];then
echo "enter the name of .jpg image without \".jpg\""
exit 0;
fi
if [ ! -f $3.jpg ];then
echo "Image not found"
exit 0;
fi
random=$RANDOM
tiltTime=$(($2/$1))
convert $3.jpg -fuzz 100% -fill white -opaque green center.jpg
for (( i=0; $i < $1; i++ )); 
do
nameOfTiltedPicture=$(($random + $i))
convert $3.jpg -rotate $i temp$nameOfTiltedPicture.jpg
composite -gravity center temp$nameOfTiltedPicture.jpg center.jpg temp$nameOfTiltedPicture.jpg
done
if [ "$4" = "" ];then
convert -delay $tiltTime temp*.jpg -loop 0 $3.gif
else
convert -delay $tiltTime temp*.jpg -loop 0 $4.gif
fi
rm temp*.jpg
rm center.jpg
