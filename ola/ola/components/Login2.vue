<template>
    <div>
        <div class="d-flex flex-row justify-content-center">
            <div class="row">
                <div class="col-md">
                    <form>
                        <div class="sign-in">Giriş Yap</div>
                        <div class="form-group">
                            <label id="words_1" for="exampleInputEmail1">Email</label>
                            <input type="email" class="form-control" id="exampleInputEmail1"
                                aria-describedby="emailHelp" placeholder="Email giriniz">
                            <small id="emailHelp" class="form-text text-muted"></small>
                        </div>
                        <div class="form-group">
                            <label id="words_2" for="exampleInputPassword1">Password &nbsp &nbsp &nbsp &nbsp &nbsp &nbsp
                                &nbsp &nbsp &nbsp &nbsp &nbsp &nbsp &nbsp &nbsp &nbsp &nbsp &nbsp &nbsp Şifrenizimi unuttunuz? </label>
                            <input type="Şifre" class="form-control" id="exampleInputPassword1"
                                placeholder="Şifre">
                            <div class="form-group">
                                <button type="button" class="btn btn-warning" id="signIn">Giriş Yap</button>
                                <p>Oturum açarak, Amazon'un Kullanım ve Satış Koşulları'nı kabul etmiş olursunuz. Kişisel verilerinizin Amazon tarafından nasıl işlendiğine ilişkin detaylı bilgi için Gizlilik Bildirimi, Çerez Bildirimi ve İlgi Alanına Dayalı Tanıtımları inceleyebilirsiniz.</p>
                                
                                 <a href="^#">Yardımamı ihtiyacınız var?</a>
                               

                            </div>
                        </div>
                        <div class="form-check">


                        </div>
                        <router-link to="SignUpPage"><button type="button" class="btn btn-warning"
                                id="grey-button">Amazon Hesabınızı Oluşturun!</button></router-link>

                    </form>
                </div>
            </div>
        </div>
    </div>
   
</template>

<script>
export default {
  data() {
    return {
      snackbar: false,
      snackbarText: 'No error message',
      auth: {
        email: '',
        password: ''
      }
    }
  },
  methods: {
    login() {
      let that = this
      this.$fire.auth.signInWithEmailAndPassword(this.auth.email, this.auth.password)
      .catch(function (error){
        that.snackbarText = error.message
        that.snackbar = true
      }).then((user) => {
        //we are signed in
        alert('deneme')
        $nuxt.$router.push('/')
      })
    },
    forgotPassword() {
      let that = this
      this.$fire.auth.sendPasswordResetEmail(this.auth.email)
      .then(function (){
        that.snackbarText = 'reset link sent to ' + that.auth.email
        that.snackbar = true
      })
      .catch(function (error) {
        that.snackbarText = error.message
        that.snackbar = true
      })
    }
  }
}
</script>