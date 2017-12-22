---
title       : 第一章
description : "本章節是我們與 R 的第一次接觸，我們將學習如何使用 R 做數學運算以及如何宣告變數，也會學習 R 的基本資料類別，讓我們趕快開始吧！"
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf



---
## 熟悉環境

你要在右邊的編輯區輸入程式來完成練習，當你按下 Submit Answer 的按鈕後，每一行程式都會被執行，R 將會回傳正確或錯誤的訊息，程式的輸出結果會呈現在右下角的 R Console 視窗中。

R 就跟 Twitter 一樣使用 `#` 來加入程式的註解，讓你與其他人可以更快了解這段程式的用途！註解不會被執行，故不影響結果，例如：在右方編輯區的第一行 _# 計算 3 + 4_ 就是註解。

若想測試語法是否正確，可以直接在 R Console 中輸入程式並按 Enter 執行。

```yaml
type: NormalExercise
key: b6d54a834f
lang: r
xp: 100
skills: 1
```


`@instructions`
- 在右邊的編輯區已經有了一些範例，你看得出來哪些是會被執行的程式，哪些是不會被執行的註解嗎？
- 加入一行程式計算 6 加 12 ，然後按下 Submit Answer。

`@hint`
參考一下範例，加入一行程式計算 6 加 12。

`@pre_exercise_code`
```{r}
# no pec
```

`@sample_code`
```{r}
# 計算 3 + 4
3 + 4

# 計算 6 + 12
```

`@solution`
```{r}
# 計算 3 + 4
3 + 4

# 計算 6 + 12
6 + 12
```

`@sct`
```{r}
test_output_contains("7", incorrect_msg = "不要把示例代码删除，再下面添加代码就好")
test_output_contains("18", incorrect_msg = "你确定你计算的是6+12吗？不要把代码写在 <code>#</code>同一行后面, 要换行！")
success_msg("Awesome! 看到命令窗口输出了计算结果了吧？let's get down to R business!")
```
---
## <<<练习1>>>

```yaml
type: MultipleChoiceExercise
key: c2c39c8d41
lang: r
xp: 50
skills: 1
```


`@instructions`

`@hint`

`@pre_exercise_code`
```{r}

```

`@sct`
```{r}

```

---
## <<<New Exercise>>>

```yaml
type: NormalExercise
key: 0cf4ca43e4
lang: r
xp: 100
skills: 1
```


`@instructions`

`@hint`

`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}

```

`@solution`
```{r}

```

`@sct`
```{r}

```

---
## <<<New Exercise>>>

```yaml
type: VideoExercise
key: c95766bc4c
lang: r
xp: 50
skills: 1
video_link: player.vimeo.com/video/154783078
```


---
## A really bad movie

```yaml
type: MultipleChoiceExercise
lang: r
xp: 50
skills: 1
key: 165b448c99
```

Have a look at the plot that showed up in the viewer to the right. Which type of movie has the worst rating assigned to it?

`@instructions`
- Adventure
- Action
- Animation
- Comedy

`@hint`
Have a look at the plot. Which color does the point with the lowest rating have?

`@pre_exercise_code`
```{r}
# The pre exercise code runs code to initialize the user's workspace.
# You can use it to load packages, initialize datasets and draw a plot in the viewer

movies <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/course/introduction_to_r/movies.csv")

library(ggplot2)

ggplot(movies, aes(x = runtime, y = rating, col = genre)) + geom_point()
```

`@sct`
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

msg_bad <- "That is not correct!"
msg_success <- "Exactly! There seems to be a very bad action movie in the dataset."
test_mc(correct = 2, feedback_msgs = c(msg_bad, msg_success, msg_bad, msg_bad))
```

---
## More movies

```yaml
type: NormalExercise
lang: r
xp: 100
skills: 1
key: 5ca00a84c9
```

In the previous exercise, you saw a dataset about movies. In this exercise, we'll have a look at yet another dataset about movies!

A dataset with a selection of movies, `movie_selection`, is available in the workspace.

`@instructions`
- Check out the structure of `movie_selection`.
- Select movies with a rating of 5 or higher. Assign the result to `good_movies`.
- Use `plot()` to  plot `good_movies$Run` on the x-axis, `good_movies$Rating` on the y-axis and set `col` to `good_movies$Genre`.

`@hint`
- Use `str()` for the first instruction.
- For the second instruction, you should use `...[movie_selection$Rating >= 5, ]`.
- For the plot, use `plot(x = ..., y = ..., col = ...)`.

`@pre_exercise_code`
```{r}
# You can also prepare your dataset in a specific way in the pre exercise code
load(url("https://s3.amazonaws.com/assets.datacamp.com/course/teach/movies.RData"))
movie_selection <- Movies[Movies$Genre %in% c("action", "animated", "comedy"), c("Genre", "Rating", "Run")]

# Clean up the environment
rm(Movies)
```

`@sample_code`
```{r}
# movie_selection is available in your workspace

# Check out the structure of movie_selection


# Select movies that have a rating of 5 or higher: good_movies


# Plot Run (i.e. run time) on the x axis, Rating on the y axis, and set the color using Genre

```

`@solution`
```{r}
# movie_selection is available in your workspace

# Check out the structure of movie_selection
str(movie_selection)

# Select movies that have a rating of 5 or higher: good_movies
good_movies <- movie_selection[movie_selection$Rating >= 5, ]

# Plot Run (i.e. run time) on the x axis, Rating on the y axis, and set the color using Genre
plot(good_movies$Run, good_movies$Rating, col = good_movies$Genre)
```

`@sct`
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

test_function("str", args = "object",
              not_called_msg = "You didn't call `str()`!",
              incorrect_msg = "You didn't call `str(object = ...)` with the correct argument, `object`.")

test_object("good_movies")

test_function("plot", args = "x")
test_function("plot", args = "y")
test_function("plot", args = "col")

test_error()

success_msg("Good work!")
```
