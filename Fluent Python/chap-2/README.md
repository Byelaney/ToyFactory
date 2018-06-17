## List Comprehensions and Readability

    symbols = "$%^&*"
    codes = []
    for symbol in symbols:
        codes.append(ord(symbol))
    codes : [36, 37, 94, 38, 42]

第一个例子使用传统 for 循环。    

    symbols = "$%^&*"
    codes = [ord(symbol) for symbol in symbols]
    codes : [36, 37, 94, 38, 42]

第二个例子使用的就是 list comprehensions，可见第二个可读性比较好。

## Listcomps Versus map and filter

下来看一下 map 和 filter，以及 python lambda。

    symbols = "$%^&*"
    codes = [ord(symbol) for symbol in symbols if ord(symbol) < 50]
    codes : [36, 37, 38, 42]

这是 listcomps 的做法，下来看一下 map 以及 filter。

    symbols = "$%^&*"
    codes = list(filter(lambda c : c < 50, map(ord, symbols)))
    codes : [36, 37, 38, 42]

## Cartesian Products

直接看例子：

    colors = ["black", "white"]
    sizes = ["S", "M", "L"]
    tshirts = [(color, size) for color in colors
                             for size in sizes]
    tshirts : [('black', 'S'), ('black', 'M'), ('black', 'L'), ('white', 'S'), ('white', 'M'), ('white', 'L')]

## Generator Expressions

初始化 tuple，array 以及其他 sequences，使用 genexp 比 listcomp 更节省内存。下面来看一个例子：

    symbols = "$%^&*"
    tuple(ord(symbol) for symbol in symbols)

genexp 的语法和 listcomp 大致相同，区别在于它使用 () 而不是 []。

# Tuples are not just immutable lists

tuple 的双重使命：immutable list 以及 records with no field names。

## Tuples as Records

    lax_coordinates = (33.9425, -118.408056)
    city, year, pop, chg, area = ("Tokyo", 2003, 32450, 0.66, 8014)
    traveler_ids = [("USA", "31195855"), ("BRA", "CE342567"), ("ESP", "XDA205856")]
    for passport in sorted(traveler_ids):
        print("%s/%s" % passport)

## Tuple Unpacking

最常见的 tuple unpacking 是 parallel assignment，如下例子：

    lax_coordinates = (33.9425, -118.408056)
    latitude, longitude = lax_coordinates # tuple unpacking

下来看一个比较优雅的例子：

    b, a = a, b

交换了两个变量。
