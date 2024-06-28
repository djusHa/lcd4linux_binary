


apt install \
  git \
  wget \
  build-essential \
  autoconf \
  libtool \
  libtool-bin \
  gettext \
  pkg-config \
  libusb-0.1-4 \
  libusb-1.0-0 \
  libusb-1.0-0-dev \
  libsqlite3-dev \
  libmariadb-dev-compat \
  checkinstall

ln -s /usr/bin/automake /usr/bin/automake-1.14
ln -s /usr/bin/aclocal /usr/bin/aclocal-1.14

git clone https://github.com/jmccrohan/lcd4linux.git

cd lcd4linux

libtoolize && automake --add-missing

./configure --prefix=/usr --bindir=/usr/sbin --with-drivers="all" --with-plugins='all,!seti,!isdn,!raspi,!xmms,!mpd,!dvb,!huawei'

make

checkinstall

wget https://netcologne.dl.sourceforge.net/project/serdisplib/serdisplib/2.02/serdisplib-2.02.tar.gz?viasf=1 -O serdisplib.tar.gz
tar -xvzf serdisplib.tar.gz
cd serdisplib-2.02
./configure --enable-libusb
make
checkinstall