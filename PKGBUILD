# Contributor: Chris Waddell <christopher at cwaddell . com >
# Contributor: Christoph Hoopmann <choopm at 0pointer.org>
# Contributor: Klaas Boesche <aurkagebe _at_ googlemail.com>
# Modified from aur package dwarffortress-mayday by
# Contributor: Patrick Chilton <chpatrick _at_ gmail _dot_ com>
# Original from community by
# Contributor: Sven-Hendrik Haase <sh@lutzhaase.com>
# Contributor: Daenyth <Daenyth+Arch [AT] gmail [DOT] com>
# Contributor: djnm <nmihalich [at} gmail dott com>

pkgname=dwarffortress-ironhand_2012
pkgver=0.34.11
_dfver=34_11
_pkgver=0.73
pkgrel=3
pkgdesc="A single-player fantasy game. You control a dwarven outpost or an adventurer in a randomly generated persistent world. Packed with Ironhand's tileset and graphics pack.  Does not replace other dwarffortress packages."
arch=(i686 x86_64)
url="http://www.bay12forums.com/smf/index.php?topic=53180.0"
install="dwarffortress-ih_2012.install"
license=('custom:dwarffortress-ih')
depends=(gcc-libs glew glu gtk2 libsndfile libxdamage ncurses openal sdl_image sdl_ttf)
makedepends=(unrar unzip git gcc-multilib)
if [[ $CARCH == 'x86_64' ]]; then
  depends=(gcc-libs-multilib lib32-glew lib32-glu lib32-gtk2 lib32-libsndfile lib32-libxdamage lib32-ncurses lib32-openal lib32-sdl_image lib32-sdl_ttf)
  optdepends=('lib32-nvidia-utils: If you have nvidia graphics'
              'lib32-catalyst-utils: If you have ATI graphics'
              'lib32-alsa-lib: for alsa sound'
              'lib32-libpulse: for pulse sound')
fi
backup=('opt/df_linux-ih2012/data/init/colors.txt'
        'opt/df_linux-ih2012/data/init/init.txt'
        'opt/df_linux-ih2012/data/init/d_init.txt'
        'opt/df_linux-ih2012/data/init/interface.txt')

source=("http://www.bay12games.com/dwarves/df_${_dfver}_linux.tar.bz2"
        "ironhand-${_pkgver}.zip::http://dffd.wimbli.com/download.php?id=6320&f=Ironhand_upgrade_${_pkgver}.zip"
		'dwarffortress-ih_2012'
		'dwarffortress-ih_2012.desktop' 
		'dwarffortress-ih_2012.png')
		
md5sums=('33e26a93e5914f7545fa1aaa53706eeb'
         '56e37b308ca5f1d5582ff82814c2649e'
         '518f3de031b4e6ea9f234abdb1db895e'
         'f9dd8b8caeca3acc806e2b86a2e3f58b'
         'b1d51f82400073af9bb179e34a9209d0')
         
_installname=df_linux-ih2012

package() {

  cd $srcdir/df_linux
  install -dm755 $pkgdir/opt/
  install -dm775 -o root -g games $pkgdir/opt/${_installname}
  cp -r $srcdir/df_linux/* $pkgdir/opt/${_installname}/
  cp -rf $srcdir/Dwarf\ Fortress/* $pkgdir/opt/${_installname}/

  find $pkgdir/opt/${_installname} -type d -exec chmod 755 {} +
  find $pkgdir/opt/${_installname} -type f -exec chmod 644 {} +

  install -Dm755 $srcdir/dwarffortress-ih_2012 $pkgdir/usr/bin/dwarffortress-ih_2012

  chmod 755 $pkgdir/opt/${_installname}/libs/Dwarf_Fortress
  
  #install -Dm755 $srcdir/${_gitname}/build/libgraphics.so $pkgdir/opt/${_installname}/libs/libgraphics.so
  ln -s /usr/lib32/libpng.so $pkgdir/opt/${_installname}/libs/libpng.so.3
  rm $pkgdir/opt/${_installname}/libs/{libgcc_s.so.1,libstdc++.so.6}

  install -d -m775 -o root -g games $pkgdir/opt/${_installname}/data/save

  chown -R root:games $pkgdir/opt/${_installname}/data
  find $pkgdir/opt/${_installname}/data -type d -exec chmod 775 {} +
  find $pkgdir/opt/${_installname}/data -type f -exec chmod 664 {} +
  chown root:games $pkgdir/opt/${_installname}

  install -Dm644 $srcdir/dwarffortress-ih_2012.desktop $pkgdir/usr/share/applications/dwarffortress-ih_2012.desktop
  install -Dm644 $srcdir/dwarffortress-ih_2012.png     $pkgdir/usr/share/pixmaps/dwarffortress-ih_2012.png

  install -Dm644 $srcdir/df_linux/readme.txt $pkgdir/usr/share/licenses/dwarffortress-ironhand_2012/readme.txt

}
