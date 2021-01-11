# kafka-connect-smt-cast

Upgraded Cast operator to deal with bytes->string cast

Cast SMT transformation for bytes -> string.
Without this fix, the conversion becomes

ByteBuffer.toString(), which always gives this useless result:

        "java.nio.HeapByteBuffer[pos=0 lim=4 cap=4]"

With this change, the byte array is converted into a hex string of the
byte buffer content, for example

        "FEDCBA9876543210"

Completed with test case and successfully tried out in a
real database conversion.
