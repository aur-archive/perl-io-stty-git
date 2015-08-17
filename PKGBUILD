# Generated by Xyne::Arch::CPAN 0.07
# Edited by wtchappell <wtchappell@gmail.com>

pkgname=perl-io-stty-git
pkgver=20100518
pkgrel=1
pkgdesc="lib/IO/Stty.pm"
arch=('i686' 'x86_64')
url="http://search.cpan.org/dist/IO-Stty/"
license=('perl')
makedepends=('perl-module-build>=0.350.0' 'git')
options=(!emptydirs)
provides=('perl-io-stty=0.30.0')
conflicts=('perl-io-stty')

_gitname=IO-Stty
_gitroot=git://github.com/gitpan/$_gitname.git

build() {

  cd $srcdir

  # Git
  msg 'Connecting to GitHub...'

  if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    msg 'Local files updated.'
  else
    git clone $_gitroot
  fi

  msg "Starting make..."

  rm -rf $srcdir/$_gitname-build
  git clone $srcdir/$_gitname $srcdir/$_gitname-build
  cd $srcdir/$_gitname-build

  # Make
  PERL_MM_USE_DEFAULT=1 perl Makefile.PL INSTALLDIRS=vendor || return 1
  make  || return 1
  make install DESTDIR="${pkgdir}" || return 1

  # remove perllocal.pod and .packlist
  find ${pkgdir} -name perllocal.pod -delete
  find ${pkgdir} -name .packlist -delete
}

# vim:set ts=2 sw=2 et:


