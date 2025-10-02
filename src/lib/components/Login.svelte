<script>
    let ipAddress = $state("");
    let username = $state("");
    let password = $state("");

    async function login() {
        try {
            const response = await fetch(`http://${ipAddress}:8080/login`, {
                method: "POST",
                headers: {
                    "Content-Type": "application/json"
                },
                body: JSON.stringify({
                    username,
                    password
                })
            });

            if (!response.ok) {
                throw new Error(`Server error: ${response.status}`);
            }

            const data = await response.json();
            console.log("Login response:", data);

            if (data.success) {
                alert("✅ Login successful!");
            } else {
                alert("❌ Invalid username or password.");
            }
        } catch (err) {
            console.error("Login failed:", err);
            alert("⚠️ Could not connect to server. Check IP or network.");
        }
    }
</script>

<!-- svelte-ignore a11y_click_events_have_key_events -->
<!-- svelte-ignore a11y_no_static_element_interactions -->
<div class="loginContainer">
    <div class="loginText">Login</div>

    <div class="inputForm">
        <div class="inputFormRow">
            <div class="inputFormText">IP Address</div>
            <input type="text" class="ipAdressInput" placeholder="192.168.1.1" bind:value={ipAddress}/>
        </div>

        <div class="inputFormRow">
            <div class="inputFormText">Username</div>
            <input type="text" class="usernameInput" placeholder="Enter your username" bind:value={username}/>
        </div>

        <div class="inputFormRow"> 
            <div class="inputFormText">Password</div>
            <input type="text" class="passwordInput" placeholder="Enter your password" bind:value={password}/>
        </div>
    </div>

    <div class="loginButton" onclick={() => login()}>
        Login
    </div>

</div>


<style>
    .loginContainer {
        position: absolute;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background-color: #1A1A1A;
        border: solid 0.3px;
        border-color: #927b12;
        border-radius: 10px;
        padding: 25px;
        top: 20%;
        left: 33%;
        width: 400px;
        gap: 10px;
    }
    .loginText {
        
    }
    .inputForm {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 15px;
        width: 100%;
    }
    .inputFormRow {
        display: flex;
        flex-direction: column;
        justify-content: center;
        width: 100%;
        gap: 3px;
    }
    .inputFormText {
        font-size: 13px;
    }
    .ipAdressInput, .usernameInput, .passwordInput {
        background-color: #0A0A0A;
        border: solid 0.3px;
        border-color: transparent;
        border-radius: 5px;
        color: white;
        padding: 5px;
    }
    .loginButton {
        background-color: #EAB308;
        border: solid 0.3px;
        border-color: transparent;
        border-radius: 5px;
        width: 100%;
        height: 25px;
        text-align: center;
        cursor: pointer;
        color: black;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        font-size: 10px;
        margin-top: 10px;
    }
</style>