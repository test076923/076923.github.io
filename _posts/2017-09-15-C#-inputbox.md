---
bg: "Clogo.jpg"
layout: post
comments: true
title:  "C# 예제 : Input Box"
crawlertitle: "C# 예제 : Input Box"
summary: "C# input box"
date: 2017-09-15
categories: exercise
tags: ['C# 예제']
author: 윤대희
star: true
---

### Input Box  ###
----------
[![1]({{ site.images }}/C/ex1/1.png)]({{ site.images }}/C/ex1/1.png)
이미지를 포함한 Input Box를 구현할 수 있습니다.

## Main ##
----------
{% highlight c# %}
public static DialogResult InputBox(string title, string content, ref string value)
{
    Form form = new Form();
    PictureBox picture = new PictureBox();
    Label label = new Label();
    TextBox textBox = new TextBox();
    Button buttonOk = new Button();
    Button buttonCancel = new Button();

    form.ClientSize = new Size(300, 100);
    form.Controls.AddRange(new Control[] { label, picture, textBox, buttonOk, buttonCancel });
    form.FormBorderStyle = FormBorderStyle.FixedDialog;
    form.StartPosition = FormStartPosition.CenterScreen;
    form.MaximizeBox = false;
    form.MinimizeBox = false;
    form.AcceptButton = buttonOk;
    form.CancelButton = buttonCancel;

    form.Text = title;
    picture.Image = Properties.Resources.Clogo;
    picture.SizeMode = PictureBoxSizeMode.StretchImage;
    label.Text = content;
    textBox.Text = value;
    buttonOk.Text = "확인";
    buttonCancel.Text = "취소";

    buttonOk.DialogResult = DialogResult.OK;
    buttonCancel.DialogResult = DialogResult.Cancel;

    picture.SetBounds(10, 10, 50, 50);
    label.SetBounds(65, 17, 100, 20);
    textBox.SetBounds(65, 40, 220, 20);
    buttonOk.SetBounds(135, 70, 70, 20);
    buttonCancel.SetBounds(215, 70, 70, 20);

    DialogResult dialogResult = form.ShowDialog();

    value = textBox.Text;
    return dialogResult;
}
{% endhighlight %}

## Use ##
----------
{% highlight C# %}
string value = "반환값";
if(InputBox("제목", "내용", ref value) == DialogResult.OK)
{ 
MessageBox.Show(value);
}
{% endhighlight %}

## Explain ##
----------
{% highlight c# %}
public static DialogResult InputBox(string title, string content, ref string value)
{% endhighlight %}
제목, 내용, 표시될 값을 받아옵니다.

{% highlight c# %}
Form form = new Form();
PictureBox picture = new PictureBox();
Label label = new Label();
TextBox textBox = new TextBox();
Button buttonOk = new Button();
Button buttonCancel = new Button();
{% endhighlight %}
사용될 컨트롤 개체를 생성합니다.

{% highlight c# %}
form.ClientSize = new Size(300, 100);
form.Controls.AddRange(new Control[] { label, picture, textBox, buttonOk, buttonCancel });
form.FormBorderStyle = FormBorderStyle.FixedDialog;
form.StartPosition = FormStartPosition.CenterScreen;
form.MaximizeBox = false;
form.MinimizeBox = false;
form.AcceptButton = buttonOk;
form.CancelButton = buttonCancel;
{% endhighlight %}
표시될 form의 상태를 설정합니다. 

* `form.ClientSize` : 폼 크기를 설정합니다. (width, height)
* `form.Controls.AddRange` : 사용되는 컨트롤 개체를 포함시킵니다.
* `form.FormBorderStyle` : 폼의 테두리를 설정합니다.
* `StartPosition` : 폼의 시작위치를 설정합니다.
* `MaximizeBox` : 최대화 단추 유/무를 설정합니다.
* `MinimizeBox` : 최소화 단추 유/무를 설정합니다.
* `AcceptButton` : Enter 키를 눌렀을 때의 실행되는 버튼을 설정합니다.
* `CancelButton` : ESC 키를 눌렀을 때의 실행되는 버튼을 설정합니다.

{% highlight c# %}
form.Text = title;
picture.Image = Properties.Resources.Clogo;
picture.SizeMode = PictureBoxSizeMode.StretchImage;
label.Text = content;
textBox.Text = value;
buttonOk.Text = "확인";
buttonCancel.Text = "취소";
{% endhighlight %}
컨트롤 개체들의 기본값을 설정합니다.

* Tip : 이미지의 경로는 Resources에 포함 시킨 후, 이미지의 파일명을 입력합니다.

{% highlight c# %}
buttonOk.DialogResult = DialogResult.OK;
buttonCancel.DialogResult = DialogResult.Cancel;
{% endhighlight %}
버튼을 눌렀을 때의 설정값을 설정합니다.

{% highlight c# %}
picture.SetBounds(10, 10, 50, 50);
label.SetBounds(65, 17, 100, 20);
textBox.SetBounds(65, 40, 220, 20);
buttonOk.SetBounds(135, 70, 70, 20);
buttonCancel.SetBounds(215, 70, 70, 20);
{% endhighlight %}
컨트롤 개체의 위치와 크기를 설정합니다. (x, y, width, height)

{% highlight c# %}
DialogResult dialogResult = form.ShowDialog();
{% endhighlight %}
설정된 폼을 띄웁니다.

{% highlight c# %}
value = textBox.Text;
return dialogResult;
{% endhighlight %}
설정된 값들을 반환합니다.

{% highlight C# %}
string value = "반환값";
if(InputBox("제목", "내용", ref value) == DialogResult.OK)
{ 
MessageBox.Show(value);
}
{% endhighlight %}
Input Box를 사용합니다.

* `value` : 초기 TextBox에 띄워질 문구를 설정합니다.
* `제목` : Form의 제목을 설정합니다.
* `내용` : Label의 내용을 설정합니다.
* `if` : `확인` 또는 `Enter`를 입력했을 때에만 작동하게 설정합니다.
* `MessageBox` : 변환된 `value`값을 확인 할 수 있습니다.
