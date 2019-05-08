all:
    # install pycocotools locally
	python setup.py build_ext --inplace
	#`(which python3 || which python)` setup.py build_ext --inplace	
	rm -rf build

install:
	# install pycocotools to the Python site-packages
	python setup.py build_ext install
	#`(which python3 || which python)` setup.py build_ext install	
	rm -rf build
