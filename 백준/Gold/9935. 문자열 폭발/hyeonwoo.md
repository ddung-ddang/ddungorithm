## 백준


- #### 9935. 문자열 폭발

<br>

## Performance

- Time : 440 ms
- Memory : 40456 KB

<br>

## Solution

```kt
fun main() {
    val br = System.`in`.bufferedReader()
    val s = br.readLine()
    val target = br.readLine()

    br.close()

    StringExplosion(s, target).simulate()
}

private class StringExplosion(
    val origin: String,
    val target: String
) {

    private val stack = ArrayDeque<Char>(origin.length)

    fun simulate() {
        stack.clear()

        for (c in origin) {
            stack += c

            if (!isMatch()) {
                continue
            }

            repeat(target.length) {
                stack.removeLast()
            }
        }

        println(stack.joinToString("").ifBlank { "FRULA" })
    }

    private fun isMatch(): Boolean {
        if (stack.size < target.length) {
            return false
        }

        var stackIdx = stack.lastIndex

        for (targetIdx in target.lastIndex downTo 0) {
            if (target[targetIdx] != stack[stackIdx]) {
                return false
            }

            stackIdx--
        }

        return true
    }

}

```
