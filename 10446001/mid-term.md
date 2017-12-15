## 說明

1. 答案直接寫在這個 `mid-term.md` 裡，並使用 Markdown 語法撰寫。
1. 題目總共分 Ruby、Rails 以及 Git 三大主題，請在每個主題完成時進行 Commit。
1. 完成後，請發送 PR 至 `mid-term` 分支。
1. 也就是說，你的 PR 應該只會有三或四次的 Commit。

## Ruby 題目 (50 分)

1. (10 分) 請完成本題實作內容

```ruby
  class Cat
    def initialize(name)
      @name = name      
    end
    def name
      @name
    end
  end

  kitty = Cat.new("kitty")
  puts kitty.name  # 在畫面上印出 kitty 字樣
```

2. (5 分) 假設有個 Hash：

```ruby
profile = {name: "kk", age: 18}
```

當執行這行程式：

```ruby
p profile["name"]
```

會得到什麼結果? 為什麼?
```
會得到nil，要寫成[:name]才會輸出"kk"的結果，因為hash中它的key為:name而不是字串，:name為符號是一個帶有名字的物件，與字串不同之處是不可變的字串，處理速度快
```

3. (5 分) 如果要在 1 到 100 的數字當中，任意取出 5 個不重複的亂數，你會怎麼做？

```
  puts [*1..100].sample(5)
```

4. (10 分)
```ruby
class Bank
  def transfer(amount)
    # ...
  end
end

Bank.transfer(10)
```

上面這段程式碼執行後會發生什麼事？為什麼？如果有錯誤又該如何修正？

```
沒有定義transfer方法

  class Bank
    def self.transfer(amount)
      puts "#{amount}"
    end
  end

  Bank.transfer(10)

```

5. (10 分) 請問以下方法：

```ruby
link_to "刪除", products_path(product), method: :delete, class: "btn btn-default"
```

`link_to` 方法共有幾個參數？為什麼？

```
3個參數，因為可以拆成link_to('刪除', products_path(product), {method: :delete, class: "btn btn-default"})，在最後一個參數{}中是放入hash，若在has中再加入多個還是算一個參數包在{}中
```

6. (10 分) 在 Ruby 裡面常會看到冒號的寫法，例如：

有的冒號靠右邊：

```ruby
class Store
  has_many :products
end
```

有的冒號靠左邊：

```ruby
link_to "檢視", books_path(book), class: "btn btn-default"
```

或是兩邊都有：

```ruby
user_profile = {name: "kk", age: 18, blood_type: :b_negative}
```

請問，這三種寫法分別代表什麼意思呢？

```
1.靠右邊:在ruby中叫做符號(symbol)是一個帶有名字的物件，也是一個類別的實體，沒辦法直接拿來當變數使用，symbol和字串的不同之處在於symbol是不可變的字串、處理速度比較快。
2.靠左邊:和一般Java寫法比較相近，class: 類別的值對應到後面的"btn btn-default"
3.兩邊都有:有一種連名帶姓的感覺、承接的意思，例如:大家都有一個叫做 Animal 的類別或是 Flyable 的模組，放在同一個專案裡就會打架了，所以設計namespace解決它，直接寫出blood_type: :b_negative，這樣就能清楚分辨
```

## Rails 題目 (30 分)

1. (10 分) 請簡述 `bundle install` 指令的用途。

```
Bundler的工具可以幫助我們檢查及安裝這個Rails應用程式所有依存的套件，每次修改gemfile就需要bundle install
```

2. (10 分) 請說明 `rails db:migrate` 這個指令的用途是什麼？

```
Migration(資料庫遷移)的用途是建立和修改資料庫資料表。Rails使用rake指令來執行Migrations。Migration的檔名中包含了Timestamp(時間戳章)，用來確保它們可以依照建立時間依序執行
```

3. (10 分) 假設某個 Controller 的程式碼如下：

```ruby
class BooksController < ApplicationController
  def index
    @books = Book.all
  end

  def update
    @book = Book.find_by(id: params[:id])
    @book.update(price: 100)
    redirect_to books_path, notice: "資料更新成功"
  end
end
```

請問：
- 第 3 行的 `@books` 前面的那個 `@` 是什麼意思？如果把 `@` 拿掉會發生什麼事？

```
@為實體變數，如果把＠拿掉的會變成區域變數，只能在index方法中執行
```

- 第 7 行以及第 8 行的 `@book`，如果把 `@` 拿掉會發生什麼事？為什麼？

```
@是指空氣中有這個值，在其他檔案中用@book餵給他傳值給他，如果拿掉會變成區域變數，在其他檔案就不能找到@book想要傳過去的值
```

## Git 題目 (20 分)

1. (10 分) 在你想像中的分支(branch)，是個什麼樣子的東西?

1. (5 分) 空的資料夾無法被加入 Git 版控，但如果就是想讓這個資料夾留下來，你會怎麼處理?

2. (5 分) 如果有些檔案，像是 `/config/database.yml` 之類比較機密的檔案，不想放在 Git 裡面，你會怎麼做？

