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

# purchase
```
    return <div>ShowTime
        <br/>
        Movieinfo<br/>
         {movie.title} <br/>{movie.description} <br/><a href={`/movie/${movie.id}`}>Movie link</a>
        <hr/>
        Showtime info<br/> {showtime.time}<br/>

        {showtime.seats} seats left <br/>
        ${showtime.price} per ticket <br/>
        <hr/>

        buy tickets:<br/>

        number: <input id="amt" type="number" onChange={calcCost}/><br/>
        
        apply discount 
        <select id="discount" onChange={calcCost}>
            <option key ="-1" value="0">None</option>
            {discounts.map((ele)=><option key={ele.id} value={ele.amount}>discount{ele.text}</option>)}
        </select> <br/>

        apply offer
        <select id="offer" onChange={calcCost}>
            <option key ="-1" value="0">None</option>
            {offers.map((ele)=><option key={ele.id} value={ele.amount}>offer{ele.text}</option>)}
        </select> <br/>

        $<p id="cost"></p>

        <button>check out</button>
    </div>
```
