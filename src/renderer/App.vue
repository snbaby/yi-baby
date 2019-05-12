<template>
    <div id="app">
        <el-button @click=start>start</el-button>
    </div>
</template>

<script>
    const puppeteer = require('puppeteer')
    export default {
      name: 'yi-baby',
      data () {
        return {
          browser: null,
          page: null
        }
      },
      created () {
        const self = this

        async function main () {
          self.browser = await puppeteer.launch({
            headless: false,
            devtools: true,
            // executablePath: `${process.cwd()}\\resources\\app.asar.unpacked\\node_modules\\puppeteer\\.local-chromium\\win64-650583\\chrome-win\\chrome.exe`,
            defaultViewport: {
              width: 1280,
              height: 800,
              deviceScaleFactor: 1,
              isMobile: true,
              hasTouch: true
            }
          })
          console.log('newPage')
          self.page = await self.browser.newPage()
          const cookies = []
          const loginStr = '{"api":"com.taobao.wireless.sys.ssoLogin","data":{"nick":"sn_baby","loginTime":"1557625853","loginCookie":["cookie2=; Domain=.etao.com; Expires=Thu, 01-Jan-1970 00:00:10 GMT; Path=/","cookie2=; Domain=.yao.95095.com; Expires=Thu, 01-Jan-1970 00:00:10 GMT; Path=/","cookie2=; Domain=.tb.cn; Expires=Thu, 01-Jan-1970 00:00:10 GMT; Path=/","cookie2=; Domain=.tdd.la; Expires=Thu, 01-Jan-1970 00:00:10 GMT; Path=/","imewweoriw=3c7k%2FwyispP01ZpwUmtghkpf8LIuutSm31GoBwoYr1k%3D; Domain=.m.taobao.com; Expires=Sun, 19-May-2019 01:50:53 GMT; Path=/","WAPFDFDTGFG=%2B4cMKKP%2B8PI%2BL9frOHE8dd0P; Domain=.m.taobao.com; Expires=Mon, 11-May-2020 01:50:53 GMT; Path=/","_w_tb_nick=sn_baby; Domain=.m.taobao.com; Expires=Sun, 19-May-2019 01:50:53 GMT; Path=/","ockeqeudmj=mJ%2Bemzo%3D; Domain=.m.taobao.com; Expires=Sun, 19-May-2019 01:50:53 GMT; Path=/","imewweoriw=3c7k%2FwyispP01ZpwUmtghkpf8LIuutSm31GoBwoYr1k%3D; Domain=.m.etao.com; Expires=Sun, 19-May-2019 01:50:53 GMT; Path=/","WAPFDFDTGFG=%2B4cMKKP%2B8PI%2BL9frOHE8dd0P; Domain=.m.etao.com; Expires=Mon, 11-May-2020 01:50:53 GMT; Path=/","_w_tb_nick=sn_baby; Domain=.m.tmall.com; Expires=Sun, 19-May-2019 01:50:53 GMT; Path=/","imewweoriw=3c7k%2FwyispP01ZpwUmtghkpf8LIuutSm31GoBwoYr1k%3D; Domain=.m.tmall.com; Expires=Sun, 19-May-2019 01:50:53 GMT; Path=/","WAPFDFDTGFG=%2B4cMKKP%2B8PI%2BL9frOHE8dd0P; Domain=.m.tmall.com; Expires=Mon, 11-May-2020 01:50:53 GMT; Path=/","_w_tb_nick=sn_baby; Domain=.m.etao.com; Expires=Sun, 19-May-2019 01:50:53 GMT; Path=/","yryetgfhth=; Domain=.login.m.taobao.com; Expires=Thu, 01-Jan-1970 00:00:10 GMT; Path=/","yryetgfhth=; Domain=.login.m.etao.com; Expires=Thu, 01-Jan-1970 00:00:10 GMT; Path=/","yryetgfhth=; Domain=.login.m.tmall.com; Expires=Thu, 01-Jan-1970 00:00:10 GMT; Path=/","unb=463920786;Domain=.taobao.com;Path=/;Expires=Sun, 19-May-2019 01:50:53 GMT;HttpOnly","tbcp=e=Vy6627f1v%2Fc6o7Qo3JW2aA%3D%3D&f=UUjZel5zvArvK4Tcy%2ByNlOadUtc%3D;Domain=.caipiao.taobao.com;Path=/;Expires=Sun, 19-May-2019 01:50:53 GMT;","uc3=nk2=EFBZxtK4Kw%3D%3D&vt3=F8dBy3qJ3A756737RAs%3D&lg2=VT5L2FSpMGV7TQ%3D%3D&id2=VypTwv1vXUPq;Domain=.taobao.com;Path=/;Expires=Tue, 11-Jun-2019 01:50:53 GMT;HttpOnly","uc1=cookie14=UoTZ48OSOfkHmQ%3D%3D&cookie15=VFC%2FuZ9ayeYq2g%3D%3D&cookie21=UIHiLt3xTIkz;Domain=.taobao.com;Path=/;Expires=Sun, 19-May-2019 01:50:53 GMT;","csg=dc87d496;Domain=.taobao.com;Path=/;Expires=Sun, 19-May-2019 01:50:53 GMT;","lgc=sn_baby;Domain=.taobao.com;Path=/;Expires=Tue, 11-Jun-2019 01:50:53 GMT;","t=d360d1c95c8137af0ff1bea07aa5a459;Domain=.taobao.com;Path=/;Expires=Sat, 10-Aug-2019 01:50:53 GMT;","cookie17=VypTwv1vXUPq;Domain=.taobao.com;Path=/;Expires=Sun, 19-May-2019 01:50:53 GMT;HttpOnly","skt=e80d13e4a39552d4;Domain=.taobao.com;Path=/;Expires=Sun, 19-May-2019 01:50:53 GMT;HttpOnly","cookie2=3c50e02c76624594ec315b693b973614;Domain=.taobao.com;Path=/;Expires=Sun, 19-May-2019 01:50:53 GMT;HttpOnly","uc4=nk4=0%40EolGnWPGn0GaP5tCk5f%2F%2F4xW&id4=0%40VX05qZjnlsjFk7XPWfOI%2BY7dV8o%3D;Domain=.taobao.com;Path=/;Expires=Tue, 11-Jun-2019 01:50:53 GMT;HttpOnly","tracknick=sn_baby;Domain=.taobao.com;Path=/;Expires=Mon, 11-May-2020 01:50:53 GMT;","_cc_=W5iHLLyFfA%3D%3D;Domain=.taobao.com;Path=/;Expires=Mon, 11-May-2020 01:50:53 GMT;","lid=;Domain=login.taobao.com;Path=/;Expires=Thu, 01-Jan-1970 00:00:00 GMT;","_l_g_=Ug%3D%3D;Domain=.taobao.com;Path=/;Expires=Sun, 19-May-2019 01:50:53 GMT;","sg=y66;Domain=.taobao.com;Path=/;Expires=Sun, 19-May-2019 01:50:53 GMT;","_nk_=sn_baby;Domain=.taobao.com;Path=/;Expires=Sun, 19-May-2019 01:50:53 GMT;","cookie1=AVNXwIRpXoAb1OPb4CDz2K8mXvrgRvJlKMPeMMEB%2FlI%3D;Domain=.taobao.com;Path=/;Expires=Sun, 19-May-2019 01:50:53 GMT;HttpOnly","_tb_token_=ebb7eeeae133e;Domain=.taobao.com;Path=/;Expires=Sun, 19-May-2019 01:50:53 GMT;"],"phone":"18502828078","userId":"463920786","sid":"3c50e02c76624594ec315b693b973614","ecode":"vMMTc"},"ret":["SUCCESS::调用成功"],"v":"3.0"}'
          const loginJson = JSON.parse(loginStr)
          console.log(loginJson.data.loginCookie)

          loginJson.data.loginCookie.forEach(temp => {
            let tempArry = temp.split(';')
            let cookieStr = tempArry[0]
            let domainStr = tempArry[1]
            const option = {
              name: cookieStr.substr(0, cookieStr.indexOf('=')),
              value: cookieStr.substr(cookieStr.indexOf('=') + 1),
              domain: domainStr.substr(domainStr.indexOf('=') + 1)
            }
            cookies.push(option)
          })
          console.log(cookies)
          await self.page.setCookie(...cookies)
          await self.page.goto('https://h5.m.taobao.com/mlapp/mytaobao.html')

          /* const cookieStr = 'imewweoriw=3ZoPrZCN6KwGlJH%2FNChs2O11fHq0jAKwMMPrbdSI7No%3D; WAPFDFDTGFG=%2B4cMKKP%2B8PI%2BL9frOHE8dd0P; _w_tb_nick=sn_baby; ockeqeudmj=nDWHPoY%3D; unb=463920786;tbcp=e=Vy6627f1v%2Fc6o7Qo3JW2aA%3D%3D&f=UUjZel5zvArvK4Tcy%2ByNlOadUtc%3D;uc3=vt3=F8dBy3qKU7zuwOaNLes%3D&nk2=EFBZxtK4Kw%3D%3D&id2=VypTwv1vXUPq&lg2=VFC%2FuZ9ayeYq2g%3D%3D;uc1=cookie21=U%2BGCWk%2F7pY%2FF&cookie14=UoTZ48D5lV%2FQAQ%3D%3D&cookie15=VT5L2FSpMGV7TQ%3D%3D;csg=2c60f741;lgc=sn_baby;t=b98e39a85f5402c22c2b2a4da8cf805b;cookie17=VypTwv1vXUPq;skt=0407b309ddb1192e;cookie2=37c50421d6f2565cda8c1be5078414a5;uc4=id4=0%40VX05qZjnlsjFk7XPWfOLKSgm%2F%2FM%3D&nk4=0%40EolGnWPGn0GaP5tCkC98W%2B1u;tracknick=sn_baby;_cc_=Vq8l%2BKCLiw%3D%3D;_l_g_=Ug%3D%3D;sg=y66;_nk_=sn_baby;cookie1=AVNXwIRpXoAb1OPb4CDz2K8mXvrgRvJlKMPeMMEB%2FlI%3D;_tb_token_=ea6b38397813e;'
                cookieStr.split(';').forEach(item => {
                  if (item.length === 0) {
                    return 0
                  }
                  const temp = item.split('=')
                  console.log(temp[0])
                  console.log(temp[1])
                  cookies.push({
                    name: temp[0].trim(),
                    value: temp[1].trim()
                  })
                })
                .版本 2

              url ＝ “https://h5.m.taobao.com/mlapp/mytaobao.html”

                await self.page.setCookie(...cookies)
                await self.page.goto('https://h5api.m.taobao.com/h5/mtop.taobao.mbis.getdeliveraddrlist')
                console.log(cookies) */
        }
        main()
      },
      methods: {
        start () {

        }
      }
    }
</script>

<style>
</style>

