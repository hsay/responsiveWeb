> ����Ϊ��ѧϰ��Ӧʽ��վ������һ��Demo,��Demo�õ���һЩ������˼����ƽʱ������Ҳ�����ã�����������õ���һЩ֪ʶ����Լ������ĿӼ�¼������

# ��Ӧʽ��վ
## ��Ŀ��ͼ
<img src="img/homeSmall.png" width="40%"/>

## �漰����
> ���Բ��֡�ý���ѯ������ӦͼƬ���ֲ�ͼ

## ý���ѯ��ʹ��
> ���������²��Դ��룺
```<html>
<head>
<style>
    h1{
        color:red;
    }
    @media only screen and (max-width: 400px) {
    body {
        background-color:red;
    }
}
</style>
</head>
    <body>
        <h1>It works hello!new</h1>
    </body>
</html>
```
> ������Ϊ�����Ϳ���ʵ������Ӧ�ˣ�����PC�ϸı��Ӵ���Сȷʵ���ԣ������ֻ��Ͳ����ˡ�
> �ֻ���ʵ������ӦҪ��ͷ���������´��룺
```
<metaname="viewport"content="width=device-width, initial-scale=1.0">
```
> ����Ҫ��һЩ��������ĳ�ʶ
* viewport ���û���ҳ�Ŀ�������
* viewport ����Ϊ���Ŀ��Խ���"����"��
* �ֻ�������ǰ�ҳ�����һ�������"����"��viewport���У�ͨ����������"����"��viewport������Ļ�������Ͳ��ð�ÿ����ҳ������С�Ĵ����У��������ƻ�û������ֻ�������Ż�����ҳ�Ĳ��֣����û�����ͨ��ƽ�ƺ�����������ҳ�Ĳ�ͬ���֡�
* width������ viewport �Ĵ�С������ָ����һ��ֵ����� 600�����������ֵ���� device-width Ϊ�豸�Ŀ�ȣ���λΪ����Ϊ 100% ʱ�� CSS �����أ���
* height���� width ���Ӧ��ָ���߶ȡ�
* initial-scale����ʼ���ű�����Ҳ���ǵ�ҳ���һ�� load ��ʱ�����ű�����
* maximum-scale�������û����ŵ�����������//���ϸ��������ֻ��ϾͲ��ܽ���������
* minimum-scale�������û����ŵ�����С������
* user-scalable���û��Ƿ�����ֶ�����
###�ӿڿ�Ⱥ��豸���
* widthֻ�ӿڿ�ȣ�device-widthΪ�豸���
####�ص�����ӿڵĸ���
> ���������������ֻ��һ���ӿڡ�
> ���Ƕ����ֻ�������������ӿڸ��
* �����ӿ�(layout viewport)
* �����ӿ�(visual viewport)
* �����ӿ�(ideal viewport)//ֻ��Ϊ�ֻ��Ż����ҳ���ʹ�ã�ʹ�÷�ʽ����<metaname="viewport"content="width=device-width, initial-scale=1.0">
�����ָ����仰�������ӿھ��ǳ��̵�Ĭ��ֵ����980px�������������仰�������ӿھ��������ӿ��ˡ�
��Ĭ������£�һ���������ƶ��豸�ϵ�viewport����Ҫ�����������������ģ�������Ϊ���ǵ��ƶ��豸�ķֱ�����������������˵���Ƚ�С������Ϊ�������ƶ��豸��������ʾ��Щ��ͳ��Ϊ�����������Ƶ���վ���ƶ��豸�ϵ������������Լ�Ĭ�ϵ�viewport��Ϊ980px��1024px��

## ����ӦͼƬ
> ����ӦͼƬ������ͼƬ��ʾ�ߴ������Ӧ��ͬʱҲ�����ͻ��˸�����������ڷ������˼��ز�ͬ��ͼƬ��
����ӦͼƬ�����ַ�ʽ��  ʹ��img��ǩ�е�srcset���ԣ�ʹ��picture��ǩ
### srcsetʵ��
```
<img src="img/ad001.png"
    srcset="img/ad001.png 480w, img/ad001-m.png 800w, img/ad001-l.png 1600w "/>
```
```
<img src="img/ad001.png"
        srcset="img/ad001.png 480w, img/ad001-m.png 800w, img/ad001-l.png 1600w">
```
> ��������ӿڴ�СΪ<=480px,�����ʾimg/ad001.png,480-800px��ʾm,����800px����ʾl.
> �����w������ǹ�����˼��������֪�����ǰ��������ͼƬ�Ĺ��������Ż���ݵ�ǰ����ʾ��Ļ(ȥƥ������ʹ���ͼƬ��ʾ)����img/ad001.png 480w���������img/ad001.png��ͼƬ�Ĺ���� 480w,��Ŀǰ�ӿ�С��480pxʱ���Ϊ480w��ͼƬ�����ʺ���ʾ�ģ����Լ��ظ�ͼƬ�������ӿ�Ϊ 500pxʱ��480w����ͼƬ�Ͳ�����Ҫ���ˣ����Ϊ800w��ͼƬ��Ϊ���ʡ�

��Ϊ����Ҫ����size,��ֵ����ʲô?
���ϵĹ�����ͼƬ����ʾռ�������ӿڡ�����������һ�����⣺
���ӿڿ��Ϊ481pxʱ����ʾ�˿��Ϊ800px��ͼƬ(�����ͼƬռ���������������ܹ����ģ���Ϊû�пռ��˷�)��
���ǣ�������ǽ�ͼƬ��ʾ���ӿڵ�һ����ʱ��?
```
<!DOCTYPE html>
<html>
<head>
    <title></title>
    <meta name="viewport" content="width=device-width,initial-scale=1" />
    <style>
        .content{
            width:50%;
            margin:0px auto;
        }
        img{
            display: block;
            width:100%;//ͼƬ��СҲ��
        }
    </style>
</head>
<body>
    <div class="content">
        <img src="img/ad001.png"
        srcset="img/ad001.png 480w, img/ad001-m.png 800w, img/ad001-l.png 1600w">
    </div>
</body>
</html>
```
��ͼƬֻ��ռ���ӿڵ�һ�룬���ӿڿ��Ϊ481pxʱ����ʾ�˿��Ϊ800px��ͼƬ(������ѡ���������Ȼ�������ӿڿ�ȣ������Ǹ���ͼƬ�İ�����ȥ�ж�/��Ϊ����Ĭ�ϵ�sizes��100vm)����ʱ800px����ʾ���ֻ��240px��
���sizeʹ�ã���size������ʱ��Ĭ��ֵ��100vm/�ӿڿ�ȣ�
����������
```
srcset="img/ad001.png 480w, img/ad001-m.png 800w, img/ad001-l.png 1600w" sizes = "50vw">
```
��ô�ͻ���viewportΪ960px��ʱ����ʾ800px��ͼƬ����ô��ʱͼƬ��ʵ����ʾ�ߴ����480px�ˣ�������֮ǰ��240px��
��ô����sizes�ж����ֵ��srcset�ж����ֵ��ʲô��ϵ��?
sizes�ж���ĳߴ���ͼƬԤ���ߴ磬����ĳ�������£�ͼƬ����ʾ�ߴ磬���������ʾ�ߴ磬������͸��ݵ�ǰͼƬ�Ĺ��ȥ��ʾ��Ӧ�ġ�
����˵������sizes= "50vw"��������ʲôý�������£�ͼƬ��Ԥ���ߴ�Ϊ50vw����viewport��һ�룬����ǰviewport�Ŀ��Ϊ960pxʱ����ʾͼƬ�Ŀ��ӦΪ480px����ô���ݸ�������srcset��������ͼƬ���ȥ������Ӧ��ͼƬ��

��sizes= "100vw"ʱ������ǰviewport���Ϊ480pxʱ��ͼƬԤ�����Ϊ100vw,��480px��(��ʱ����ʵ��ͼƬ�İ�����)����ô������ͻ�ѡ��800px��ͼƬ����ʵ��ʱͼƬ�¼���ʾ�Ŀ����240px��.
### ʵ��
```
<!DOCTYPE html>
<html>
<head>
    <title></title>
    <meta name="viewport" content="width=device-width,initial-scale=1" />
    <style>
        .content{
            width:100%;
            margin:0px auto;
        }
        img{
            display: block;
            /*width:100%;*/
            max-width: 100%;
        }
    </style>
</head>
<body>
    <!-- <div class="content">
        <img src="img/ad001.png"
        srcset="img/ad001.png 480w, img/ad001-m.png 800w, img/ad001-l.png 1600w"
        sizes="10vm">
    </div> -->
    <div class="content">
        <img src="img/mm-width-128px.jpg"
        srcset="img/mm-width-128px.jpg 128w, img/mm-width-256px.jpg 256w, img/mm-width-512px.jpg 512w"
        sizes="(min-width : 256px) 256px, 100vw">
    </div>
</body>
</html>
```
���ϴ�����Ҫʵ�ֵĹ��ܣ���viewport��ȴ��ڵ���256pxʱ����ʾ256px��ͼƬ��ͼƬʵ����ʾ�ߴ�Ϊ256px�����������ʾͼƬ��ʵ�ʳߴ�Ϊ��ǰviewport�Ŀ��

��ѡ���ͼƬ��viewport�Ŀ�ȴ���256ʱѡ��   256pxͼƬ������С��ʱѡ��128px.
ͼƬ���Ԥ�� 50vw��sizes="50vw"��

### �ܽ�
srcset������һЩͼƬ������ÿ��ͼƬ�ĵ�ַ�͹�񣩣���������Ը��ݵ�ǰʵ�����ȥѡ����������ͼƬ��
sizes���Ը���ý���ѯȥ�趨��Ҫ��ʾͼƬ�ĳߴ磬������������ϣ����ʵ�ʵ�srcset��ͼƬ������ȥѡ��ͼƬ��

### picture��ǩ
����ý���ѯ��img������Ӧ��srcset
```
<picture>
    <source media="(max-width:30em)" srcset="1.png 528w"/>
    <source srcset="2.png 228w"/>
    <img src="3.png"  />
</picture>
```
���Ǹ���ý���ѯ������ͼƬѡ��Ҳ����˵��������˽ϴ��ͼƬ��viewport��Сʱ�������¼��ؽ�С��ͼƬ��������֮ǰ�����˴�ͼƬ��һֱ��ʾ��
ƥ�䵽source֮�󣬸�srcset����Ϊimg�������ˡ���ƥ�䲻�ϣ�ֱ��ʹ��img��


