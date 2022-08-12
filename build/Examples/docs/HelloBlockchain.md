
<a name="0x779698c80d691ed95f85196125eec43cc40491048eacd2b9bd26ec1307ed311b_message"></a>

# Module `0x779698c80d691ed95f85196125eec43cc40491048eacd2b9bd26ec1307ed311b::message`



-  [Resource `MessageHolder`](#0x779698c80d691ed95f85196125eec43cc40491048eacd2b9bd26ec1307ed311b_message_MessageHolder)
-  [Function `set_message`](#0x779698c80d691ed95f85196125eec43cc40491048eacd2b9bd26ec1307ed311b_message_set_message)


<pre><code><b>use</b> <a href="">0x1::signer</a>;
<b>use</b> <a href="">0x1::string</a>;
</code></pre>



<a name="0x779698c80d691ed95f85196125eec43cc40491048eacd2b9bd26ec1307ed311b_message_MessageHolder"></a>

## Resource `MessageHolder`



<pre><code><b>struct</b> <a href="HelloBlockchain.md#0x779698c80d691ed95f85196125eec43cc40491048eacd2b9bd26ec1307ed311b_message_MessageHolder">MessageHolder</a> <b>has</b> key
</code></pre>



<details>
<summary>Fields</summary>


<dl>
<dt>
<code><a href="HelloBlockchain.md#0x779698c80d691ed95f85196125eec43cc40491048eacd2b9bd26ec1307ed311b_message">message</a>: <a href="_String">string::String</a></code>
</dt>
<dd>

</dd>
</dl>


</details>

<a name="0x779698c80d691ed95f85196125eec43cc40491048eacd2b9bd26ec1307ed311b_message_set_message"></a>

## Function `set_message`



<pre><code><b>public</b> <b>fun</b> <a href="HelloBlockchain.md#0x779698c80d691ed95f85196125eec43cc40491048eacd2b9bd26ec1307ed311b_message_set_message">set_message</a>(account: <a href="">signer</a>, message_bytes: <a href="">vector</a>&lt;u8&gt;)
</code></pre>



<details>
<summary>Implementation</summary>


<pre><code><b>public</b> entry <b>fun</b> <a href="HelloBlockchain.md#0x779698c80d691ed95f85196125eec43cc40491048eacd2b9bd26ec1307ed311b_message_set_message">set_message</a>(account: <a href="">signer</a>, message_bytes: <a href="">vector</a>&lt;u8&gt;)
<b>acquires</b> <a href="HelloBlockchain.md#0x779698c80d691ed95f85196125eec43cc40491048eacd2b9bd26ec1307ed311b_message_MessageHolder">MessageHolder</a> {
    <b>let</b> <a href="HelloBlockchain.md#0x779698c80d691ed95f85196125eec43cc40491048eacd2b9bd26ec1307ed311b_message">message</a> = <a href="_utf8">string::utf8</a>(message_bytes);
    <b>let</b> account_addr = <a href="_address_of">signer::address_of</a>(&account);
    <b>if</b> (!<b>exists</b>&lt;<a href="HelloBlockchain.md#0x779698c80d691ed95f85196125eec43cc40491048eacd2b9bd26ec1307ed311b_message_MessageHolder">MessageHolder</a>&gt;(account_addr)) {
        <b>move_to</b>(&account, <a href="HelloBlockchain.md#0x779698c80d691ed95f85196125eec43cc40491048eacd2b9bd26ec1307ed311b_message_MessageHolder">MessageHolder</a> {
            <a href="HelloBlockchain.md#0x779698c80d691ed95f85196125eec43cc40491048eacd2b9bd26ec1307ed311b_message">message</a>,
        })
    } <b>else</b> {
        <b>let</b> old_message_holder = <b>borrow_global_mut</b>&lt;<a href="HelloBlockchain.md#0x779698c80d691ed95f85196125eec43cc40491048eacd2b9bd26ec1307ed311b_message_MessageHolder">MessageHolder</a>&gt;(account_addr);
        old_message_holder.<a href="HelloBlockchain.md#0x779698c80d691ed95f85196125eec43cc40491048eacd2b9bd26ec1307ed311b_message">message</a> = <a href="HelloBlockchain.md#0x779698c80d691ed95f85196125eec43cc40491048eacd2b9bd26ec1307ed311b_message">message</a>;
    }
}
</code></pre>



</details>
