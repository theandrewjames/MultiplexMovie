* for React html pages
* crystal will put crude html with important things js will check for - ie id, name, onClick, {variable}
* ana can add finished html/css underneath ?


# forgotpw
```
<div>
    <div id="recAcc">
        Forgot password but remember your email? recover your account:
        <input id="recEmail"/>
        <button onClick={(e)=>findAcc(e)}>recover acc</button>
        {/* success: hide recAcc, unhide secCheck (class hidden)
            fail: emNotFound text = No account has been registered with that email */}
        <div id="emNotFound"></div>
    </div>

    <div id="secCheck" class = "hidden">
        {secQ /*laoded from user table*/}
        <input id="secA"/>
        <button onClick={(e) => {checkSecQ(e)}}>confirm security question</button>
        {/* success: redirect to reset path
            fail: secfail text = Security check failed */}
        <div id="secFail"></div>
    </div>
</div>
```
# reset pw
```
<div>
    {email} <br/>
    <input id="newpw"/><br/>
    <input id="newpw2"/><br/>
    <button onClick={(e)=>resetPw(e)}>Reset password</button>
    {/* success: update user table, resetResult text = Reset successful
        fail: secfail text = New passwords don't match */}
    <div id="resetResult"></div>
</div>
```
