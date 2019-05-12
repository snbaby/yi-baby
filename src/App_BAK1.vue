<template>
    <div id="app">
        {{message}}
        <el-button @click=getQrLoginImg>获取二维码</el-button>
        <el-button @click=loginCheck>检查是否已登录</el-button>
        <canvas id="qrLoginImg" width="200" height="100"></canvas>
    </div>
</template>

<script>
    const request = require('request')
    var QRCode = require('qrcode')
    const randomString = function (len) {
      len = len || 32
      const chars = 'ABCDEFGHJKMNOPQRSTUVWXYZ0123456789'
      const maxPos = chars.length
      let pwd = ''
      for (let i = 0; i < len; i++) {
        pwd += chars.charAt(Math.floor(Math.random() * maxPos))
      }
      return pwd
    }
    export default {
      name: 'yi-baby',
      data () {
        return {
          qrLoginUrl: '',
          lgToken: '',
          adToken: '',
          message: '请获取二维码',
          token: '',
          appkey: '21646297',
          appsecret: 'f2438a7500e0d6ac7535327b67b67b8e',
          api: 'com.taobao.mtop.login.loginByKey',
          v: '1.0',
          Imei: randomString(15),
          imsi: randomString(15),
          deviceId: randomString(32)

        }
      },
      created () {
      },
      methods: {
        getQrLoginImg () {
          const self = this
          const option = {
            url: 'https://qrlogin.taobao.com/qrcodelogin/generateQRCode4Login.do?dsp=%E6%B7%98TV&shortURL=true',
            jar: true,
            headers: {
              'User-Agent': 'request'
            }
          }
          request.get(option, (error, response, body) => {
            if (!error) {
              const result = JSON.parse(body)
              console.log(result)
              if (result.success) {
                self.qrLoginUrl = result.url
                self.lgToken = result.lgToken
                self.adToken = result.adToken
                QRCode.toCanvas(document.getElementById('qrLoginImg'), self.qrLoginUrl, function (error) {
                  if (error) {
                    console.error(error)
                    self.message = '二维码获取失败,请重新获取二维码'
                  } else {
                    self.message = '二维码获取成功,请扫描二维码,扫描二维码后,请检查是否已登录'
                  }
                  console.log('success!')
                })
              }
            }
          })
        },
        loginCheck () {
          const self = this
          const option = {
            url: `https://qrlogin.taobao.com/qrcodelogin/qrcodeLoginCheck.do?lgToken=${self.lgToken}&lt=m`,
            jar: true,
            headers: {
              'User-Agent': 'request'
            }
          }
          request.get(option, (error, response, body) => {
            if (!error) {
              const result = JSON.parse(body)
              console.log(result)
              if (result.code === '10000') {
                setTimeout(self.loginCheck(), 1000)
              } else if (result.code === '10001') {
                setTimeout(self.loginCheck(), 1000)
              } else if (result.code === '10004') {
                self.getQrLoginImg()
                self.message = '二维码扫描失败，请重新扫描二维码后，请检查是否已登录'
              } else {
                self.token = result.token
              }
            } else {
              self.getQrLoginImg()
              self.message = '二维码扫描失败，请重新扫描二维码后，请检查是否已登录'
            }
          })
        }
      }
    }
</script>

<style>
</style>

