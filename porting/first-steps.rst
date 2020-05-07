
İLK ADIMLAR
===========

Bu sayfa, Halium Portlamaya başlatmak için atmanız gereken ilk adımları içerir.

.. _support-channels:

Yardım alma
------------

Port işlemi sırasında herhangi bir noktada takılırsanız, size yardımcı olmak için buradayız! Aşağıdaki destek kanallarından bize ulaşabilirsiniz:

* IRC: #halium on Freenode
* Matrix: #halium:disroot.org
* Telegram: @halium

Bizimle iletişime geçtiğinizde, Hataları bildirmek için lütfen Pastebin hizmeti kullanın: `pastebin.com <https://pastebin.com>`_ . 

Hedef Android cihazı seçin.
-----------------------------

Buradaysanız, muhtemelen Portlamak istediğiniz bir cihazınız var demektir. Ancak, yine de aşağıdaki gereksinimleri karşılayan cihazlara Portlamanızı öneririz:

Kaynak kodu bulunabilirliği
    Cihazınızın Linux çekirdek kaynağı herkese açık olmalıdır. LineageOS 12.1 veya 14.1'i derlemek için gereken kaynak kodu da mevcut olmalıdır. Cihazınızın bir LineageOS 12.1 veya 14.1 portu veya bu versiyonlara dayalı bir LineageOS türevi portu varsa bunların her ikisi de mevcut olmalıdır.

Çekirdek (Kernel)
    Halium şu anda Linux çekirdek sürümü 3.10.0 veya daha büyük olan bir cihaz gerektirir. `systemd v217 README'ye göre <https://github.com/systemd/systemd/blob/v217/README#L40>`_, eski aygıt çekirdekleri systemd v217 veya daha yenisi ile uyumlu değildir. Android Chazınızın hakkında sayfasında “Çekirdek Sürümü” nü bularak cihazınızın çekirdek sürümünü öğrenebilirsiniz. Ayarıca Çekirden kaynak kodundan ``Makefile`` içinden bulabilirsiniz.

RAM
    1GB Ram ile Çoğu Halium dağıtımı sorunsuz çalıştırılabilir. Daha iyi son kullanıcı deneyimi için 2GB önerilir.

Depolama
    16GB depolamaya ihtiyaç vardır. Daha düşük boyutlarda bazı halium dağıtımları için yetersiz depolama sorunu oluşturabilir.


Cihazınız bu gereksinimleri karşılamıyorsa Halium'u oluşturabilir ve çalıştırabilirsiniz. Cihazınızın gereksinimleri karışlayıp karşılamadığından emin değilseniz :ref:`contact us <support-channels>`

Collaborate
-----------

Head over to the  `list of ports <https://github.com/Halium/projectmanagement/issues>`_ and check if someone is already working on this device. If it is started, collaborate with those porters.

Document your target device
---------------------------

Head over to :doc:`/supplementary/how-to-document` to learn about adding your device's information to our device overview. Adding your device will also lead you to looking at other Halium devices, some of which may have similar hardware to yours. You can use fixes made in similar devices to fix your own.

Set up your build device
------------------------

Now you will need to install packages on the computer you wish to build Halium with.

Debian (Stretch or newer) / Ubuntu (16.04 or newer)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you are on the ``amd64`` architecture (commonly referred to as 64 bit), enable the usage of the ``i386`` architecture::

   sudo dpkg --add-architecture i386

Update your package lists to take advantage of the new architecture::

    sudo apt update

Install the required dependencies::

   sudo apt install git gnupg flex bison gperf build-essential \
     zip bzr curl libc6-dev libncurses5-dev:i386 x11proto-core-dev \
     libx11-dev:i386 libreadline6-dev:i386 libgl1-mesa-glx:i386 \
     libgl1-mesa-dev g++-multilib mingw-w64-i686-dev tofrodos \
     python-markdown libxml2-utils xsltproc zlib1g-dev:i386 schedtool \
     repo liblz4-tool bc lzop imagemagick libncurses5 rsync

Arch
^^^^

If you have an ``amd64`` installation of Arch, you need to add the ``[multilib]`` repository to your ``/etc/pacman.conf`` . This will allow you to install and run ``i686`` packages. Please refer to `'Official Repositories/multilib' on the Arch Wiki <https://wiki.archlinux.org/index.php/multilib>`_.

Install the ``base-devel`` package if you have not already.

Install the required dependencies from AUR::

   git clone https://aur.archlinux.org/halium-devel.git && cd halium-devel && makepkg -i

.. Note::
    Arch uses Python 3 as its default ``python``, which may cause some errors while building. Using a Python 2 virtualenv is highly recommended. Please refer to `'Python/Virtual environment' on the Arch Wiki <https://wiki.archlinux.org/index.php/Python/Virtual_environment>`_ for instructions on setting up a Virtual Environment.
