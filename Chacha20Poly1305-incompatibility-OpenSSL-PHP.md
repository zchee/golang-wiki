Greetings! I would like to know how to implement OpenSSL-PHP compatible Chacha20-Poly1305 and AES-256-GCM algorithms but I'm having problems: 

```php
<?php
$plaintext = 'SECRET MESSAGE';
$key = '820qufp5820qufp5820qufp5820qufp5';
$nonce = '000000000000';
$r = openssl_encrypt(
    $plaintext,
    'chacha20-poly1305',
    $key, 
    $options=1,
    $nonce
);

echo base64_encode($r);

echo "<br>";

$t = openssl_decrypt(
    $r,
    'chacha20-poly1305',
    $key, 
    $options=1,
    $nonce
);
echo $t;
?>
```

Result:
`6N/wRtwz/VhHOfyepNk=`

Equivalent to:
```go
	out := aead.Seal(nil, nonce, msg, nil)
	fmt.Printf("%s", out[:len(msg)])
```

(If I don't truncate* the output, the result is:
`6N/wRtwz/VhHOfyepNnnYKagDMd4Gk9HPSv2y1EWros=`)

But there is no way to decrypt it in Go as the ciphertext has no tag:
```go
	out, err := aead.Open(nil, nonce, msg, nil)
	if err != nil {
		log.Fatal(err)
	}
	fmt.Printf("%s", out)
```

Result:
`chacha20poly1305: message authentication failed`

It's not compatible with OpenSSL-PHP?