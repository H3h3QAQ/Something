# Go实现简单的图书管理系统

```go
package main

import (
	"fmt"
	"os"
)

/**
 @author:H3h3QAQ
 @一个简单的图书管理系统
 */
var book = make(map[string]books,5000)

type books struct {
	title string
	author string
	price float32
	status string
}

func addBooks(b map[string]books)  {
	p:=books{}
	var n string
	fmt.Println("请根据提示输入相关内容")
	fmt.Print("请输入书名：")
	fmt.Scanln(&p.title)
	fmt.Print("请输入作者：")
	fmt.Scanln(&p.author)
	fmt.Print("请输入价格：")
	fmt.Scanln(&p.price)
	fmt.Print("请输入是否上架(Y|N)")
	fmt.Scanln(&n)
	if(n == "Y") {
		p.status="已上架"
	}
	if(n=="N"){
		p.status="未上架"
	}
	b[p.title] =p
}
func delBooks(b map[string]books)  {
	var n string
	fmt.Println("请根据提示输入相关内容")
	fmt.Print("请输入想要删除的书名")
	fmt.Scanln(&n)
	if(judge(n,b)==true){
		delete(b,n)
	}else {
		fmt.Println("您要删除的书不存在")
	}
}
func allBooks(b map[string]books)  {
	if len(b)== 0{
		fmt.Println("目前没有书籍")
	}
	for _,v :=range b{
		fmt.Println(v)
	}
}
func judge(k string,b map[string]books) bool {
	_,a := b[k]
	return a
}
func changeBook(b map[string]books)  {
	var a string
	p:=books{}
	fmt.Print("请输入您要修改的书名：")
	fmt.Scanln(&a)
	if judge(a,b)==true{
		delete(b,a)
		fmt.Print("请输入修改后的书名：")
		fmt.Scanln(&p.title)
		fmt.Print("请输入修改后书的作者名字：")
		fmt.Scanln(&p.author)
		fmt.Print("请输入修改后的书的价格：")
		fmt.Scanln(&p.price)
		p.status="已上架"
		b[p.title]=p
	}else {
		fmt.Println("您要修改的书不存在")
	}
}
func borow(b map[string]books)  {
	var a string
	p:=books{}
	fmt.Print("请输入您要借阅的书名：")
	fmt.Scanln(&a)
	if (judge(a,b)==true) {
		p=b[a]
		p.status="已被借阅"
		delete(b,a)
		b[p.title]=p
		fmt.Println("借阅成功")
	}else {
		fmt.Println("未收录该书籍")
	}
}
func returnBook(b map[string]books)  {
	var a string
	p:=books{}
	fmt.Print("请输入您要归还的书名：")
	fmt.Scanln(&a)
	if(judge(a,b)==true){
		p=b[a]
		p.status="已上架"
		delete(b,a)
		b[p.title]=p
		fmt.Println("归还成功")

	}else {
		fmt.Println("未借阅本书籍")
	}
}
func showMenu()  {
	fmt.Println("欢迎登录本系统")
	fmt.Println(">>1.添加书籍")
	fmt.Println(">>2.删除书籍")
	fmt.Println(">>3.展示所有书籍")
	fmt.Println(">>4.修改书籍")
	fmt.Println(">>5.借阅书籍")
	fmt.Println(">>6.归还书籍")
	fmt.Println(">>7.退出")
}
func drawtop()  {
	fmt.Println("                                         Welcome to the library management system                                         ")
	fmt.Println("**************************************************************************************************************************")
}
func drawlow()  {
	fmt.Println("**************************************************************************************************************************")
}
func drawline()  {
	fmt.Println("--------------------------------------------------------------------------------------------------------------------------")
}
func main()  {
	for   {
		drawtop()
		showMenu()
		drawlow()
		var option int
		fmt.Scanln(&option)
		switch option {
		case 1:
			drawline()
			addBooks(book)
			drawline()
		case 2:
			drawline()
			delBooks(book)
			drawline()
		case 3:
			drawline()
			allBooks(book)
			drawline()
		case 4:
			drawline()
			changeBook(book)
			drawline()
		case 5:
			drawline()
			borow(book)
			drawline()
		case 6:
			drawline()
			returnBook(book)
			drawline()
		case 7:
			fmt.Println("感谢使用！")
			os.Exit(0)

		}

	}
}
```

