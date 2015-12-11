# deepdetect

Full instruction at [http://www.deepdetect.com/tutorials/imagenet-classifier/](http://www.deepdetect.com/tutorials/imagenet-classifier/)

To enable API access outside of virtual machine:

* Enable port forwarding in Vagrantfile
* run `dede` with `-host 0.0.0.0` option

Run DeepDetect image classifier:

    cd /opt/deepdetect/build/main/
    sudo ./dede &
    curl -X PUT "http://localhost:8080/services/imageserv" -d "{\"mllib\":\"caffe\",\"description\":\"image classification service\",\"type\":\"supervised\",\"parameters\":{\"input\":{\"connector\":\"image\"},\"mllib\":{\"template\":\"googlenet\",\"nclasses\":1000}},\"model\":{\"templates\":\"../templates/caffe/\",\"repository\":\"../../models/imgnet\"}}"

Testing image classification:

    curl -X POST "http://localhost:8080/predict" -d "{\"service\":\"imageserv\",\"parameters\":{\"input\":{\"width\":224,\"height\":224},\"output\":{\"best\":3}},\"data\":[\"https://upload.wikimedia.org/wikipedia/commons/4/45/A_small_cup_of_coffee.JPG\"]}"