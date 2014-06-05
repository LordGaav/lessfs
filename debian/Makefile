KEY=CD9C0E84
DIST=trusty
TARBALL=../lessfs-1.7.0.orig.tar.gz
SRCROOT=lessfs-1.7.0

package:
	dpkg-buildpackage -A -us -uc
 
generate_control:
	cat debian/control.source debian/control.precise > debian/control

source: generate_control
	dpkg-buildpackage -S -k$(KEY)

source_no_sign: generate_control
	dpkg-buildpackage -S -us -d
 
upload_to_ppa:
	dput ppa:lordgaav/lessfs "$(CHANGES)"

clean:
	rm debian/control
	rm -R src || exit 0
	rmdir etc || exit 0

pbuild:
	pbuilder-dist "$(DIST)" "$(CHANGES)"

unzip_source: clean
	tar xvf "$(TARBALL)" "$(SRCROOT)"
	mv "$(SRCROOT)" src
