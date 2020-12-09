mysqldump --databases [DATABASE_NAME] \
-h [INSTANCE_IP] -u [USERNAME] -p [PASSWORD] \
--hex-blob --default-character-set=utf8mb4 | sed 's/ENGINE=MyISAM/ENGINE=InnoDB/g' > [DATABASE_FILE].sql