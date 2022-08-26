From d330b99bee87ec80b834033b1d682fa3b3238818 Mon Sep 17 00:00:00 2001
From: dharmicksai <dharmicksaik@gmail.com>
Date: Fri, 26 Aug 2022 22:06:49 +0530
Subject: [PATCH] Add check for CONFIG_CGROUP_BPF in check-config.sh

cgroup v2 requires CONFIG_CGROUP_BPF kernel option to be set
else runc can not start containers.

check-config.sh script checks if the CONFIG_CGROUP_BPF option
is set. As this is available from kerenl 4.15 a version gaurd
is included to check CONFIG_CGROUP_BPF. The check is present
under Optional Features.

Closes #3547

Signed-off-by: dharmicksai <dharmicksaik@gmail.com>
---
 script/check-config.sh | 4 ++++
 1 file changed, 4 insertions(+)

diff --git a/script/check-config.sh b/script/check-config.sh
index ec8bc63a57..e3bde47606 100755
--- a/script/check-config.sh
+++ b/script/check-config.sh
@@ -274,6 +274,10 @@ if kernel_lt 5 0; then
 	check_flags IOSCHED_CFQ CFQ_GROUP_IOSCHED
 fi
 
+if ! kernel_lt 4 14; then
+	check_flags CGROUP_BPF
+fi
+
 flags=(
 	BLK_CGROUP BLK_DEV_THROTTLING
 	CGROUP_PERF