---
layout: post
title:  "ESI to SII binary"
date:   2016-06-28
comments: true
tags: esi sii ethercat microcontroller somanet synapticon
---

For the purpose of this post we'll use [SOMANET COM EtherCAT][com-ethercat] controller board. Our goal is to:

- generate SII binaries from ESI files,
- write SII contents to a slave and
- print EEPROM content in a human-readable format.

Prerequisites
-------------

1. [SOMANET COM EtherCAT][com-ethercat] as a communication module along with [SOMANET Core C22][core-c22].

   <blockquote class="instagram-media" data-instgrm-captioned data-instgrm-version="7" style=" background:#FFF; border:0; border-radius:3px; box-shadow:0 0 1px 0 rgba(0,0,0,0.5),0 1px 10px 0 rgba(0,0,0,0.15); margin: 1px; max-width:658px; padding:0; width:99.375%; width:-webkit-calc(100% - 2px); width:calc(100% - 2px);"><div style="padding:8px;"> <div style=" background:#F8F8F8; line-height:0; margin-top:40px; padding:41.5277777778% 0; text-align:center; width:100%;"> <div style=" background:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACwAAAAsCAMAAAApWqozAAAABGdBTUEAALGPC/xhBQAAAAFzUkdCAK7OHOkAAAAMUExURczMzPf399fX1+bm5mzY9AMAAADiSURBVDjLvZXbEsMgCES5/P8/t9FuRVCRmU73JWlzosgSIIZURCjo/ad+EQJJB4Hv8BFt+IDpQoCx1wjOSBFhh2XssxEIYn3ulI/6MNReE07UIWJEv8UEOWDS88LY97kqyTliJKKtuYBbruAyVh5wOHiXmpi5we58Ek028czwyuQdLKPG1Bkb4NnM+VeAnfHqn1k4+GPT6uGQcvu2h2OVuIf/gWUFyy8OWEpdyZSa3aVCqpVoVvzZZ2VTnn2wU8qzVjDDetO90GSy9mVLqtgYSy231MxrY6I2gGqjrTY0L8fxCxfCBbhWrsYYAAAAAElFTkSuQmCC); display:block; height:44px; margin:0 auto -44px; position:relative; top:-22px; width:44px;"></div></div> <p style=" margin:8px 0 0 0; padding:0 4px;"> <a href="https://www.instagram.com/p/BHRv2bzDSvB/" style=" color:#000; font-family:Arial,sans-serif; font-size:14px; font-style:normal; font-weight:normal; line-height:17px; text-decoration:none; word-wrap:break-word;" target="_blank">#somanet #c22 #ethercat #synapticon</a></p> <p style=" color:#c9c8cd; font-family:Arial,sans-serif; font-size:14px; line-height:17px; margin-bottom:0; margin-top:8px; overflow:hidden; padding:8px 0 7px; text-align:center; text-overflow:ellipsis; white-space:nowrap;">A photo posted by Marko (@ce_la_vii) on <time style=" font-family:Arial,sans-serif; font-size:14px; line-height:17px;" datetime="2016-06-30T11:41:13+00:00">Jun 30, 2016 at 4:41am PDT</time></p></div></blockquote><script async defer src="//platform.instagram.com/en_US/embeds.js"></script>

2. Installed [IgH EtherCAT Master for Linux][igh-ethercat-master]. [Synapticon][synapticon] has prepared an installer for EtherCAT master drive that you can [download from here][ethercat-master-software].
3. [siitool][siitool] developed by fjeschke at [Synapticon][synapticon]. This tool will help us generate SSI binaries and view EtherCAT EEPROM content in a human-readable format.

Generate SII binaries from ESI files
------------------------------------

Use siitool to generate binary from the existing [Somanet_CiA402-single.xml][somanet-cia402-single] like in the example or any other ESI file:

    $ ./siitool -o esi.bin Somanet_CiA402-single.xml

Write SII contents to a slave
-----------------------------

Use ethercat tool to write the generated binary to EEPROM of the first EtherCAT slave on the bus:

    $ ethercat sii_write -p 0 esi.bin

Print EEPROM content in a human-readable format
-----------------------------------------------

The ethercat command-line tool already comes with commands for reading the EEPROM content. For example `ethercat xml` generates slave information XML and `ethercat sii_read` outputs slave's SSI contents in a binary or a textual representation. You can also use siitool -p flag to print SII contents in a human-readable format:

    $ ethercat sii_read > esi.bin
    $ ./siitool -p esi.bin

which prints identity, default mailbox settings, supported mailboxes, EEPROM size and version, FMMU, SM, TxPDO, RxPDO etc.

[com-ethercat]: https://doc.synapticon.com/hardware/com-ethercat/revision-a4/index.html
[core-c22]: https://doc.synapticon.com/hardware/core-c22/revision-a5/index.html
[igh-ethercat-master]: http://www.etherlab.org/en/ethercat/
[synapticon]: https://www.synapticon.com/
[ethercat-master-software]: https://doc.synapticon.com/tutorials/ethercat_master_software/index.html
[siitool]: https://github.com/synapticon/siitool
[somanet-cia402-single]: https://github.com/sncn-private/EtherCAT_Misc/blob/master/Somanet_ESI/Somanet_CiA402-single.xml
