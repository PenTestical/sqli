# SQL Injection - All-in-One Fuzzing Wordlist

![image](https://user-images.githubusercontent.com/57206134/126528848-d717c286-83df-4a10-9167-fe8e1eb713ae.png)

To test for SQL Injections, different wordlists can be used. This is a merged wordlist, which contains generic SQLi payloads for MySQL, NoSQL, MSSQL, Oracle, etc. It has all sort of SQLi payload types (time-based, error-based, generic payloads, etc.). Instead of using multiple wordlists, you can quickly identify vulnerable endpoints with one wordlist. Depending on the result, further analysis can be done. 

## Example usage for GET requests

`wfuzz -c -z file,/usr/share/wfuzz/wordlist/Injections/hugeSQL.txt "http://127.0.0.1/index.php?id=FUZZ"`

## Example usage for POST requests

`wfuzz -c -z file,/usr/share/wfuzz/wordlist/Injections/hugeSQL.txt -d "username=admin\&password=FUZZ" http://127.0.0.1/admin`

## Filter out the important result with wfuzz

By using wfuzz's own filter, you can define a baseline and filter out unnecassary responses.

### Hiding responses with X chars

After your first wfuzz scan, you should get multiple responses with X chars. For example, `X = 0` chars. To filter these out, specify the option:

`--hh 0`

### Hiding responses with X words

In a same manner, you can filter out responses with X words. For example, for `X = 1` word. Use the wfuzz flag:

`--hw 1`

You can also use `--hl 1` or `--hc 1` to filter out results with 1 line or 1 specified code, respectively. 

