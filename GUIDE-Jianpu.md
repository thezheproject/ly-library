# 简谱转写指南

（由阿里通义 Qwen2.5-72B-Instruct 开源模型提供，Diamochang 整理。对该指南内容的问题可以通过 Issue 提出。）

将简谱转写成 Jianpu-ly 可以识别的格式，需要根据简谱的具体内容和 Jianpu-ly 支持的语法进行转换。以下是一些基本步骤和示例：

## 1. **基础音符**
   - **音高**：简谱中的数字对应 Jianpu-ly 中的音符。例如，简谱中的 `1` 对应 `1`，`2` 对应 `2`，依此类推。
   - **八度**：简谱中的音高可以通过在数字后加逗号或单引号来表示不同的八度。例如，`1` 为中音，`1,` 为低八度，`1'` 为高八度。
   - **升降号**：简谱中的升降号可以通过 `#` 和 `b` 来表示。例如，`#1` 表示升1，`b2` 表示降2。

   **示例**：
   ```plaintext
   简谱: 1 2 3 4 5 6 7 1'
   Jianpu-ly: 1 2 3 4 5 6 7 1'
   ```

## 2. **节奏**
   - **四分音符**：简谱中的四分音符直接对应 Jianpu-ly 中的 `1`。
   - **八分音符**：简谱中的八分音符对应 Jianpu-ly 中的 `q1`。
   - **十六分音符**：简谱中的十六分音符对应 Jianpu-ly 中的 `s1`。
   - **附点音符**：简谱中的附点音符可以通过在音符后加点来表示。例如，附点四分音符 `1.` 对应 `1.`。

   **示例**：
   ```plaintext
   简谱: 1 2 3 4 5 6 7 1' 1. 2.
   Jianpu-ly: 1 2 3 4 5 6 7 1' 1. 2.
   ```

## 3. **休止符**
   - **四分休止符**：简谱中的四分休止符对应 Jianpu-ly 中的 `R`。
   - **八分休止符**：简谱中的八分休止符对应 Jianpu-ly 中的 `qR`。
   - **十六分休止符**：简谱中的十六分休止符对应 Jianpu-ly 中的 `sR`。

   **示例**：
   ```plaintext
   简谱: 1 0 2 0 3 0
   Jianpu-ly: 1 R 2 R 3 R
   ```

## 4. **连音线和圆滑线**
   - **连音线**：简谱中的连音线可以通过 `~` 来表示。例如，`1 ~ 1` 表示两个音符连在一起。
   - **圆滑线**：简谱中的圆滑线可以通过 `(` 和 `)` 来表示。例如，`1 ( 2 )` 表示两个音符之间有一个圆滑线。

   **示例**：
   ```plaintext
   简谱: 1 - 1
   Jianpu-ly: 1 ~ 1
   ```

## 5. **和弦**
   - **和弦**：简谱中的和弦可以通过在音符之间加空格来表示。例如，`1 3 5` 表示一个 C 大三和弦。

   **示例**：
   ```plaintext
   简谱: 1 3 5
   Jianpu-ly: 1 3 5
   ```

## 6. **歌词**
   - **歌词**：简谱中的歌词可以通过 `L:` 来表示。歌词内容需要放在 `L:` 后面，并且在同一行上。

   **示例**：
   ```plaintext
   简谱: 1 2 3 4 5 6 7 1'
   歌词: 这是歌词
   Jianpu-ly: 1 2 3 4 5 6 7 1'
   L: 这 是 歌 词
   ```

## 7. **其他符号**
   - **拍号**：简谱中的拍号可以通过 `4/4` 来表示。
   - **调号**：简谱中的调号可以通过 `1=Bb` 来表示。
   - **速度**：简谱中的速度可以通过 `4=85` 来表示。

   **示例**：
   ```plaintext
   简谱: 4/4 1=Bb 4=85
   Jianpu-ly: 4/4 1=Bb 4=85
   ```

## 8. **多声部和多次演奏**
在 Jianpu-ly 中表示多声部音乐，可以使用 `NextPart` 命令来分隔不同的声部。每个声部可以有自己的乐器、调号、拍号等设置。以下是一些具体的步骤和示例。

### **分隔声部**
   - 使用 `NextPart` 命令来分隔不同的声部。
   - 每个声部可以有自己的乐器设置，通过 `instrument=...` 来指定。

### **设置声部信息**
   - **调号**：使用 `1=Bb` 等命令来设置调号。
   - **拍号**：使用 `4/4` 等命令来设置拍号。
   - **速度**：使用 `4=85` 等命令来设置速度。

### **编写音符**
   - 每个声部的音符按照 Jianpu-ly 的语法编写。

### 示例

假设我们有两个声部，一个高音部和一个低音部，我们可以这样编写：

```plaintext
% 高音部
instrument=Flute
1=Bb
4/4
4=85

1 2 3 4 5 6 7 1'
1 2 3 4 5 6 7 1'
1 2 3 4 5 6 7 1'
1 2 3 4 5 6 7 1'

NextPart

% 低音部
instrument=Cello
1=Bb
4/4
4=85

5 6 7 1'
5 6 7 1'
5 6 7 1'
5 6 7 1'
```

### 详细解释

1. **高音部**：
   - `instrument=Flute`：指定高音部的乐器为长笛。
   - `1=Bb`：设置调号为 Bb 大调。
   - `4/4`：设置拍号为 4/4。
   - `4=85`：设置速度为每分钟 85 拍。
   - 音符部分：编写高音部的音符。

2. **分隔声部**：
   - `NextPart`：分隔高音部和低音部。

3. **低音部**：
   - `instrument=Cello`：指定低音部的乐器为大提琴。
   - `1=Bb`：设置调号为 Bb 大调。
   - `4/4`：设置拍号为 4/4。
   - `4=85`：设置速度为每分钟 85 拍。
   - 音符部分：编写低音部的音符。

### 更复杂的示例

假设我们有一个包含更多细节的多声部简谱，可以这样编写：

```plaintext
% 高音部
instrument=Flute
1=Bb
4/4
4=85

1 2 3 4 5 6 7 1'
1. 2. 3. 4. 5. 6. 7. 1.'
1 - 2 - 3 - 4 - 5 - 6 - 7 - 1' -
1 ~ 2 ~ 3 ~ 4 ~ 5 ~ 6 ~ 7 ~ 1'

NextPart

% 低音部
instrument=Cello
1=Bb
4/4
4=85

5 6 7 1'
5. 6. 7. 1.'
5 - 6 - 7 - 1' -
5 ~ 6 ~ 7 ~ 1'

NextPart

% 低音部（第二部分）
instrument=Cello
1=Bb
4/4
4=85

1, 2, 3, 4,
1, 2, 3, 4,
1, 2, 3, 4,
1, 2, 3, 4,
```

### 详细解释

1. **高音部**：
   - 包含不同类型的音符（四分音符、附点音符、连音线等）。

2. **分隔声部**：
   - `NextPart`：分隔高音部和低音部。

3. **低音部**：
   - 包含不同类型的音符（四分音符、附点音符、连音线等）。

4. **低音部（第二部分）**：
   - 使用 `NextPart` 再次分隔，表示低音部的第二部分。

### 多次演奏
简谱中的多次演奏可以通过 `NextScore` 来表示。

## 9. **循环、重复**
在 Jianpu-ly 中表示一段乐曲的循环，可以使用 `R{ ... }` 和 `A{ ... }` 命令来实现。这些命令分别用于表示重复段落和重复段落的不同结尾。

### **基本重复**
   - 使用 `R{ ... }` 来表示一个简单的重复段落。

### **带交替结尾的重复**
   - 使用 `A{ ... }` 来表示重复段落的不同结尾。

### 示例

假设我们有一段简谱，包含一个重复段落和两个不同的结尾，可以这样编写：

```plaintext
% 设置调号、拍号和速度
1=C
4/4
4=85

% 乐曲的开头部分
1 2 3 4 5 6 7 1'

% 重复段落
R{
  1 2 3 4
  5 6 7 1'
}

% 第一个结尾
A{
  1 2 3 4
}

% 第二个结尾
A{
  5 6 7 1'
}

% 乐曲的结尾部分
1 2 3 4 5 6 7 1'
```

### 详细解释

1. **设置调号、拍号和速度**：
   - `1=C`：设置调号为 C 大调。
   - `4/4`：设置拍号为 4/4。
   - `4=85`：设置速度为每分钟 85 拍。

2. **乐曲的开头部分**：
   - `1 2 3 4 5 6 7 1'`：乐曲的开头部分。

3. **重复段落**：
   - `R{ 1 2 3 4 5 6 7 1' }`：表示这部分音乐将被重复一次。

4. **第一个结尾**：
   - `A{ 1 2 3 4 }`：表示在第一次重复后使用这个结尾。

5. **第二个结尾**：
   - `A{ 5 6 7 1' }`：表示在第二次重复后使用这个结尾。

6. **乐曲的结尾部分**：
   - `1 2 3 4 5 6 7 1'`：乐曲的结尾部分。

### 更复杂的示例

假设我们有一段更复杂的简谱，包含多个重复段落和交替结尾，可以这样编写：

```plaintext
% 设置调号、拍号和速度
1=C
4/4
4=85

% 乐曲的开头部分
1 2 3 4 5 6 7 1'

% 第一个重复段落
R{
  1 2 3 4
  5 6 7 1'
}

% 第一个结尾
A{
  1 2 3 4
}

% 第二个结尾
A{
  5 6 7 1'
}

% 第二个重复段落
R{
  1 3 5 7
  1' 3' 5' 7'
}

% 第三个结尾
A{
  1 3 5 7
}

% 第四个结尾
A{
  1' 3' 5' 7'
}

% 乐曲的结尾部分
1 2 3 4 5 6 7 1'
```

### 详细解释

1. **设置调号、拍号和速度**：
   - `1=C`：设置调号为 C 大调。
   - `4/4`：设置拍号为 4/4。
   - `4=85`：设置速度为每分钟 85 拍。

2. **乐曲的开头部分**：
   - `1 2 3 4 5 6 7 1'`：乐曲的开头部分。

3. **第一个重复段落**：
   - `R{ 1 2 3 4 5 6 7 1' }`：表示这部分音乐将被重复一次。

4. **第一个结尾**：
   - `A{ 1 2 3 4 }`：表示在第一次重复后使用这个结尾。

5. **第二个结尾**：
   - `A{ 5 6 7 1' }`：表示在第二次重复后使用这个结尾。

6. **第二个重复段落**：
   - `R{ 1 3 5 7 1' 3' 5' 7' }`：表示这部分音乐将被重复一次。

7. **第三个结尾**：
   - `A{ 1 3 5 7 }`：表示在第一次重复后使用这个结尾。

8. **第四个结尾**：
   - `A{ 1' 3' 5' 7' }`：表示在第二次重复后使用这个结尾。

9. **乐曲的结尾部分**：
   - `1 2 3 4 5 6 7 1'`：乐曲的结尾部分。

## 10. **特殊符号**
   - **装饰音**：简谱中的装饰音可以通过 `g[...]` 来表示。
   - **颤音**：简谱中的颤音可以通过 `///` 来表示。

   **示例**：
   ```plaintext
   简谱: 1 装饰音 1 颤音
   Jianpu-ly: 1 g[1] 1 ///
   ```

## 11. **其他 Lilypond 代码**
   - **Lilypond 代码**：简谱中需要使用 Lilypond 代码的部分可以通过 `LP:` 和 `:LP` 来表示。

   **示例**：
   ```plaintext
   简谱: 1 (Lilypond 代码)
   Jianpu-ly: 1
   LP: \someLilypondCode
   :LP
   ```
   
## 注释源码（供核对、修正和补充）

```plaintext
Text files are whitespace-separated and can contain:
Scale going up: 1 2 3 4 5 6 7 1'
Accidentals: 1 #1 2 b2 1
Octaves: 1,, 1, 1 1' 1''
Shortcuts for 1' and 2': 8 9
Percussion beat: x
Change base octave: < >
Semiquaver, quaver, crotchet (16/8/4th notes): s1 q1 1
Dotted versions of the above (50% longer): s1. q1. 1.
Demisemiquaver, hemidemisemiquaver (32/64th notes): d1 h1
Minims (half notes) use dashes: 1 -
Dotted minim: 1 - -
Semibreve (whole note): 1 - - -
Time signature: 4/4
Time signature with quaver anacrusis (8th-note pickup): 4/4,8
Key signature (major): 1=Bb
Key signature (minor): 6=F#
Tempo: 4=85
Lyrics: L: here are the syl- la- bles (all on one line)
Lyrics (verse 1): L: 1. Here is verse one
Lyrics (verse 2): L: 2. Here is verse two
Hanzi lyrics (auto space): H: hanzi (with or without spaces)
Lilypond headers: title=the title (on a line of its own)
Guitar chords: chords=c2. g:7 c (on own line)
Fret diagrams: frets=guitar (on own line)
Multiple parts: NextPart
Instrument of current part: instrument=Flute (on a line of its own)
Multiple movements: NextScore
Prohibit page breaks until end of this movement: OnePage
Suppress bar numbers: NoBarNums
Suppress first-line indent: NoIndent
Ragged last line: RaggedLast
Old-style time signature: SeparateTimesig 1=C 4/4
Indonesian 'not angka' style: angka
Add a Western staff doubling the tune: WithStaff
Tuplets: 3[ q1 q1 q1 ]
Grace notes before: g[#45] 1
Grace notes after: 1 ['1]g
Grace notes with durations: g[d4d5s6] 1
Simple chords: ,13'5 1 1b3 1 (chord numbers are sorted automatically)
Da capo: 1 1 Fine 1 1 1 1 1 1 DC
Repeat (with alternate endings): R{ 1 1 1 } A{ 2 | 3 }
Short repeats (percent): R4{ 1 2 }
Ties (like Lilypond's, if you don't want dashes): 1 ~ 1
Slurs (like Lilypond's): 1 ( 2 )
Erhu fingering (applies to previous note): Fr=0 Fr=4
Erhu symbol (applies to previous note): souyin harmonic up down bend tilde
Tremolo: 1/// - 1///5 -
Rehearsal letters: letterA letterB
Multibar rest: R*8
Dynamics (applies to previous note): \p \mp \f
Other 1-word Lilypond \ commands: \fermata \> \! \( \) etc
Text: ^"above note" _"below note"
Harmonic symbols above main notes: Harm: (music) :Harm (main music)
Other Lilypond code: LP: (block of code) :LP (each delimeter at start of its line)
Unicode approximation instead of Lilypond: Unicode
Ignored: % a comment
```