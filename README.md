Correct following error of MindTheGapps-13.0.0-arm-20231025_200806 on Xperia Z Tablet SGP312 using TWRP3.7.0.9.

    Can not found a storage device name of /system. Orignal META-INF/com/google/android/update-binary scpipt may unmatch format of /etc/recovery.fstab on SGP312. I correct statements are:

    Old) grep -v "^#" /etc/recovery.fstab | grep "[[:blank:]]$1[[:blank:]]" | tail -n1 | tr -s [:blank:] ' ' | cut -d' ' -f1

    New) cat /etc/recovery.fstab | cut -d '#' -f 1 | grep /system | grep -o '/dev/[^ ]*' | head -1

    No files are copied to /system. The copy command of TWRP3.7 can not support "--preserve" option. So copy command has failed. The option should be same "-p".

    Old) cp --preserve=a -r ./* "${SYSTEM_OUT}/"

    New) cp -pr ./* "${SYSTEM_OUT}/"

