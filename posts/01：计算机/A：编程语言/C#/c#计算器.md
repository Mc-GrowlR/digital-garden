# 出现的问题
## 结果显示错误
描述：最后一位不显示，结果错误
~~~ C#
if(j == 0)
     num1 = Convert.ToDouble(lblShow.Text.Substring(0));
else
     num1 = Convert.ToDouble(lblShow.Text.Substring(0,j));
if (lblShow.Text.Length-1>=j+1)
     num2 = Convert.ToDouble(lblShow.Text.Substring(j+1));
                        //lblShow.Text = lblShow.Text.Substring(j+1);
                    result = num1 + num2;
                    string str1 = result.ToString();
                    lblShow.Text += buttonOperator.Text;
~~~

原因是其中的提取字符串函数阐述设置错误。

