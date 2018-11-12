<template>
    <div>
        <form action="j_security_check" method="POST">
        <label for="j_username">username:</label>
        <input id="j_username" size="20" />
        <br />

        <label for="j_password">password:</label>
        <input id="j_password" size="20"/>
        <br />

        <input type="submit" value="Login" />
        </form>
    </div>
</template>