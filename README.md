# need-decoding-From f0592192193e6d33646e448633cd285c0ce1db1b Mon Sep 17 00:00:00 2001
From: Marin <m.dzhigarov@gmail.com>
Date: Mon, 18 Nov 2013 13:08:56 +0200
Subject: [PATCH] Added new icons for the Otr padlock button. Fixed a memory
 leak with the Otr padlock button.

---
 resources/images/images.properties                 |   4 +-
 .../images/plugin/otr/encrypted_verified22x22.png  | Bin 0 -> 1561 bytes
 resources/images/plugin/otr/padlockBrokenOpen.png  | Bin 0 -> 1572 bytes
 resources/images/plugin/otr/padlockLoading.gif     | Bin 0 -> 419 bytes
 resources/images/plugin/otr/plaintext22x22.png     | Bin 408 -> 1456 bytes
 resources/languages/resources.properties           |   2 +
 .../plugin/desktoputil/SIPCommButton.java          |   7 +
 .../communicator/plugin/otr/OtrContactMenu.java    | 171 +++------------------
 .../plugin/otr/OtrMetaContactButton.java           | 152 +++++++++---------
 .../communicator/plugin/otr/OtrTransformLayer.java |  16 +-
 .../communicator/plugin/otr/OtrWeakListener.java   | 155 +++++++++++++++++++
 .../sip/communicator/plugin/otr/ScOtrEngine.java   |   9 +-
 .../communicator/plugin/otr/ScOtrEngineImpl.java   | 114 +++++++++++++-
 .../communicator/plugin/otr/ScSessionStatus.java   |  29 ++++
 14 files changed, 423 insertions(+), 236 deletions(-)
 create mode 100644 resources/images/plugin/otr/encrypted_verified22x22.png
 create mode 100644 resources/images/plugin/otr/padlockBrokenOpen.png
 create mode 100644 resources/images/plugin/otr/padlockLoading.gif
 create mode 100644 src/net/java/sip/communicator/plugin/otr/OtrWeakListener.java
 create mode 100644 src/net/java/sip/communicator/plugin/otr/ScSessionStatus.java

diff --git a/resources/images/images.properties b/resources/images/images.properties
index c02cec9..e9a729f 100644
--- a/resources/images/images.properties
+++ b/resources/images/images.properties
@@ -536,13 +536,15 @@ plugin.securityconfig.ICON=resources/images/plugin/securityconfig/security.png
 
 # otr plugin icons
 plugin.otr.ENCRYPTED_ICON_16x16=resources/images/plugin/otr/encrypted16x16.png
-plugin.otr.ENCRYPTED_ICON_22x22=resources/images/plugin/otr/encrypted22x22.png
+plugin.otr.ENCRYPTED_ICON_22x22=resources/images/plugin/otr/encrypted_verified22x22.png
 plugin.otr.ENCRYPTED_UNVERIFIED_ICON_16x16=resources/images/plugin/otr/encrypted_unverified16x16.png
 plugin.otr.ENCRYPTED_UNVERIFIED_ICON_22x22=resources/images/plugin/otr/encrypted_unverified22x22.png
 plugin.otr.PLAINTEXT_ICON_16x16=resources/images/plugin/otr/plaintext16x16.png
 plugin.otr.PLAINTEXT_ICON_22x22=resources/images/plugin/otr/plaintext22x22.png
 plugin.otr.FINISHED_ICON_16x16=resource
