* for React html pages
* crystal will put crude html with important things js will check for - ie id, name, onClick, {variable}
* ana can add finished html/css underneath ?


# forgotpw
```
    return <div>
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
            {/* success: hide secCheck, set reset to resetpw component
                fail: secfail text = Security check failed */}
            <div id="secFail"></div>
        </div>

        {reset}
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
         {movie.title} <br/>{movie.description} <br/>
        <hr/>
        location info<br/>
        {location.name}<br/>
        {location.notifs}
        <hr/>
        Showtime info<br/> {showtime.time}<br/>

        {showtime.seats} seats left <br/>
        ${showtime.price} per ticket <br/>
        <hr/>

        buy tickets:<br/>
    <form>
        number: <input id="amt" type="number" min="1" onChange={calcCost}/><br/>
        
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

        <button onClick={(e)=>{purchase(e)}}>check out</button>
        </form>
    </div>
```

# movies: all and by multiplex
```
    return <div>
        Multiplex <select id="multiplex" onChange={setAll}>
            <option>All</option>
            {multiplexes.map((ele)=><option>{ele.name}</option>)}
        </select>

        {movies.map(
            (movie)=><div>
                {movie.title}<br/>
                {movie.showtimes.map((stid) => <a href={`/showtime/${stid}`}>{getShowtimeTime(stid)}</a>)}
            </div>
        )}
    </div>
```

# multiplexes
```
    return <div>
        Multiplexes
        <button onClick={addMultiplex}>add new multiplex</button>
        {/* newMultiplex becomes AddMultiplex component */}

        {myMultiplexes.map(
            (mult)=><div key={mult.id} >
                <div>{mult.name}</div>

                {getShowTimes(mult.id).map((st)=> <a href={`/showtime/${st.id}`}>{st.time} {st.title}</a>)}
                <br/>
                
                <button onClick={()=>addShowTime(mult.id)}>add showtime</button>
                {/* newShowTime becomes NewShowComponent */}

        </div>
        )}
        
        {/* starts as an empty div */}
        {newMultiplex}

        {/* starts as an empty div */}
        {newShowTime}
    </div>

```
