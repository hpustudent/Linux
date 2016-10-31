## shell的两种执行命令方式，交互和批处理
    #!/bin/sh 是约定标记，告诉系统脚本需要的解释器，这里指向的是/bin/bash,除了这个，之后的所有#都表示注释
    echo 是输出文本命令， echo -e 执行转义后输出
### 运行shell脚本的两种方式
    1. shell保存为文件，chmod +x ./test.sh 添加可执行权限，执行./test.sh即可
    2. 使用/bin/sh test.sh 作为sh的参数执行，这种运行的脚本，就不需要在第一行执行解释器了
### shell常用命令
    1. read 从stdin输入，可以使用`read NAME`,表示从stdin输入并赋值给NAME变量
    2. readonly 将变量定义为只读，只读变量不能被修改
    3. unset 删除变量，变量被删除后不能再次使用，不能删除只读变量
    4. 特殊变量
         1. $0 当前脚本的文件名
         2. $n 传递给脚本或函数的参数，第一个参数为$1 ，第二个为$2
         3. $# 传递给脚本或者函数的个数
         4. $@ 传递给脚本或者函数的所有参数
         5. $* 传递给脚本或者函数的所有参数
         6. $? 上个命令的退出状态，或函数返回值
         7. $$ 当前shell进程id
    5. 字符串
         1. 获取字符串长度 ${#string}
         2. 提取子串 ${string:1:4}
         3. 查找字符串 ${}
    6. 命令替换$(command) 
    7. 数组
         1. 支持一维数组，下标从0开始
         2. 大括号表示数组，元素用空格分隔开，persons=(person1 person2 person3)
         3. 可以不使用连续的下标，下标的范围没有限制
         4. 读取数组元素 ${persons[0]}
         5. 使用@或者*可以读取数组中所有元素${persons[*]}或者${persons[@]}
    8. shell运算符
         1. 原生bash不支持数学运算，可以通过命令实现，expr最常用
         2. 使用expr命令时，表达式和运算符要有空格，必须是2 + 2，完整的表达式要被``包含
         3. 加减乘除取余实现，乘法运算用\*符号实现
         4. 条件表达式要放在方括号之间，并且要有空格 [ $a == $b ]不相等用[ $a != $b ]
         5. 关系运算符只支持数字，不支持字符串[ $a -eq $b ] [ $a -ne $b ]   
         [ $a -gt $b ] [ $a -lt $b ] [ $a -ge $b ] [ $a -le $b ] !为非运算，-o为或运算 -a为与运算
         6. 字符串运算符[ $a = $b ] [ $a != $b ] [ -z $a ]判断字符串长度是否为0，  
         为0返回true，[ -n $a ]判断字符串长度是否为0，不为0返回true，[ $a ]检测字符串是否为空，不为空返回true
         7. 文件测试运算符
              1. [ -r $file ] 是否有读权限
              2. [ -w $file ] 是否有写权限
              3. [ -x $file ] 是否有执行权限
              4. [ -e $file ] 文件是否存在
              5. [ -s $file ] 文件大小是否为0，文件是否为空
              6. [ -d $file ] 文件是否是目录
              7. [ -f $file ] 文件是否是普通文件
         8. 条件判断
              1. 无条件继续执行用分号
              2. 前一个条件正确则执行下一个用&&
              3. 前一个条件不正确则执行下一个用||
              4. if ... fi 语句
                    if [ expression ]
                    then 
                       some statements
                    fi
              5. if ... else ... fi语句
                    if [ expression ]
                    then
                       some statements
                    else
                       some statements
                    fi
              6. if ... elif ... else ... fi语句
                    if [ expression ]
                    then
                      some statements
                    elif [ expression ]
                    then 
                      some statements
                    elif [ expression ]
                    then
                      some statemens
                    else
                      some statemens
                    fi
              7. test 命令替换[ expression ]检测某个条件是否成立
              8. case语句使用，值必须为常数或者变量，;;表示break，跳出
                    case 值 in
                    模式1)
                        command1
                        ;;
                    模式2）
                        command2
                        ;;
                    *)
                        command3
                        ;;
                    esac
              9. for循环语句使用，列表是数字或者字符串组成的序列，每个值通过空格分割，也可以不加in，  
              没有in的时候，使用命令行位置参数
                    for 变量 in 列表
                    do
                        command1
                        command2
                        ...
                        commandN
                    done
              10. while循环语句使用
                    while command
                    do
                       Statement(s) to be executed if command is true
                    done
              11. until 循环语句使用
                    until command
                    do
                       Statement(s) to be executed until command is true
                    done
              12. 定义函数，方式为,可以增加return语句执行返回值，如果不加，会将最后一句命令运行结果作为返回值，  
              函数返回值可以通过$?获得，  
              调用函数时可以向其传递参数，函数体内部，通过${n}获取参数的值
                    func_name(){
                      [return value]
                    }
                    
              
              
              
                    

    > 注意：shell定义变量时，变量名和=之间不能留有空格，使用定义过的变量，只要在变量名前家$或者${}，  
    单引号字符串中的变量无效，双引号中可以有变量
