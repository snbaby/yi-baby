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
    let a = 'imewweoriw=3czY3NAUFKX7NTDJX94DtYvFB3Kc3Ec2V3XlI2sx2Pk%3D; WAPFDFDTGFG=%2B4cMKKP%2B8PI%2BuXLRuA5amyp5Yc%2FedcY%3D; _w_tb_nick=%E5%86%B0%E5%B0%B9%E5%A4%A9%E4%BE%9D; ockeqeudmj=jfnH0hc%3D; unb=771970063;tbcp=e=D8zmosM6YGGSAQ7D4nxqkDNmdOU%3D&f=UUjZelvMEgfJRd0TJUhnU%2BM4U8c%3D;uc3=id2=VAYpwWXjJILx&nk2=0rzL0TnNV0Q%3D&vt3=F8dBy3qKUBsSemPfnOo%3D&lg2=VT5L2FSpMGV7TQ%3D%3D;uc1=cookie14=UoTZ48D5nLsTYw%3D%3D&cookie15=W5iHLLyFOGW7aA%3D%3D&cookie21=Vq8l%2BKCLjA%2Bl;csg=5b31e8f0;lgc=%5Cu51B0%5Cu5C39%5Cu5929%5Cu4F9D;t=88640c9808bc7dab6b82afd68701fac8;cookie17=VAYpwWXjJILx;skt=43a3d747edc1e3cc;cookie2=3a89085ece725b54b54a8a52f0c59f60;uc4=id4=0%40Vh%2B7t76PIxXY58YCKXkA7OZMie4%3D&nk4=0%400A3UK%2FIUZ3YqdashFJiPnX7rFA%3D%3D;tracknick=%5Cu51B0%5Cu5C39%5Cu5929%5Cu4F9D;_cc_=WqG3DMC9EA%3D%3D;_l_g_=Ug%3D%3D;sg=%E4%BE%9D34;_nk_=%5Cu51B0%5Cu5C39%5Cu5929%5Cu4F9D;cookie1=UNX7u0bc0PxpCK1r%2BRXJe9lEOozJ797M3ZotDyGxeDM%3D;_tb_token_=f34ea7711bbb5;'
    let b = 'imewweoriw=3czY3NAUFKX7NTDJX94DtYvFB3Kc3Ec2V3XlI2sx2Pk%3D; WAPFDFDTGFG=%2B4cMKKP%2B8PI%2BuXLRuA5amyp5Yc%2FedcY%3D; _w_tb_nick=%E5%86%B0%E5%B0%B9%E5%A4%A9%E4%BE%9D; ockeqeudmj=jfnH0hc%3D; unb=771970063;tbcp=e=D8zmosM6YGGSAQ7D4nxqkDNmdOU%3D&f=UUjZelvMEgfJRd0TJUhnU%2BM4U8c%3D;uc3=id2=VAYpwWXjJILx&nk2=0rzL0TnNV0Q%3D&vt3=F8dBy3qKUBsSemPfnOo%3D&lg2=VT5L2FSpMGV7TQ%3D%3D;uc1=cookie14=UoTZ48D5nLsTYw%3D%3D&cookie15=W5iHLLyFOGW7aA%3D%3D&cookie21=Vq8l%2BKCLjA%2Bl;csg=5b31e8f0;lgc=%5Cu51B0%5Cu5C39%5Cu5929%5Cu4F9D;t=88640c9808bc7dab6b82afd68701fac8;cookie17=VAYpwWXjJILx;skt=43a3d747edc1e3cc;cookie2=3a89085ece725b54b54a8a52f0c59f60;uc4=id4=0%40Vh%2B7t76PIxXY58YCKXkA7OZMie4%3D&nk4=0%400A3UK%2FIUZ3YqdashFJiPnX7rFA%3D%3D;tracknick=%5Cu51B0%5Cu5C39%5Cu5929%5Cu4F9D;_cc_=WqG3DMC9EA%3D%3D;_l_g_=Ug%3D%3D;sg=%E4%BE%9D34;_nk_=%5Cu51B0%5Cu5C39%5Cu5929%5Cu4F9D;cookie1=UNX7u0bc0PxpCK1r%2BRXJe9lEOozJ797M3ZotDyGxeDM%3D;_tb_token_=f34ea7711bbb5;'
    console.log(a.split(';'))
    console.log(b.split(';'))

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
      const loginStr = '{"api":"com.taobao.wireless.sys.ssoLogin","data":{"nick":"sn_baby","loginTime":"1557564344","loginCookie":["cookie2=; Domain=.etao.com; Expires=Thu, 01-Jan-1970 00:00:10 GMT; Path=/","cookie2=; Domain=.yao.95095.com; Expires=Thu, 01-Jan-1970 00:00:10 GMT; Path=/","cookie2=; Domain=.tb.cn; Expires=Thu, 01-Jan-1970 00:00:10 GMT; Path=/","cookie2=; Domain=.tdd.la; Expires=Thu, 01-Jan-1970 00:00:10 GMT; Path=/","imewweoriw=3ZwaQfGeHBUkdsjX4a6Emh9C5bk8cIHgwA4Z5JteX%2Bo%3D; Domain=.m.taobao.com; Expires=Sat, 18-May-2019 08:45:44 GMT; Path=/","WAPFDFDTGFG=%2B4cMKKP%2B8PI%2BL9frOHE8dd0P; Domain=.m.taobao.com; Expires=Sun, 10-May-2020 08:45:44 GMT; Path=/","_w_tb_nick=sn_baby; Domain=.m.taobao.com; Expires=Sat, 18-May-2019 08:45:44 GMT; Path=/","ockeqeudmj=uB8MkRs%3D; Domain=.m.taobao.com; Expires=Sat, 18-May-2019 08:45:44 GMT; Path=/","imewweoriw=3ZwaQfGeHBUkdsjX4a6Emh9C5bk8cIHgwA4Z5JteX%2Bo%3D; Domain=.m.etao.com; Expires=Sat, 18-May-2019 08:45:44 GMT; Path=/","WAPFDFDTGFG=%2B4cMKKP%2B8PI%2BL9frOHE8dd0P; Domain=.m.etao.com; Expires=Sun, 10-May-2020 08:45:44 GMT; Path=/","_w_tb_nick=sn_baby; Domain=.m.tmall.com; Expires=Sat, 18-May-2019 08:45:44 GMT; Path=/","imewweoriw=3ZwaQfGeHBUkdsjX4a6Emh9C5bk8cIHgwA4Z5JteX%2Bo%3D; Domain=.m.tmall.com; Expires=Sat, 18-May-2019 08:45:44 GMT; Path=/","WAPFDFDTGFG=%2B4cMKKP%2B8PI%2BL9frOHE8dd0P; Domain=.m.tmall.com; Expires=Sun, 10-May-2020 08:45:44 GMT; Path=/","_w_tb_nick=sn_baby; Domain=.m.etao.com; Expires=Sat, 18-May-2019 08:45:44 GMT; Path=/","yryetgfhth=; Domain=.login.m.taobao.com; Expires=Thu, 01-Jan-1970 00:00:10 GMT; Path=/","yryetgfhth=; Domain=.login.m.etao.com; Expires=Thu, 01-Jan-1970 00:00:10 GMT; Path=/","yryetgfhth=; Domain=.login.m.tmall.com; Expires=Thu, 01-Jan-1970 00:00:10 GMT; Path=/","unb=463920786;Domain=.taobao.com;Path=/;Expires=Sat, 18-May-2019 08:45:44 GMT;HttpOnly","tbcp=f=UUjZel5zvArvK4Tcy%2ByNlOadUtc%3D&e=Vy6627f1v%2Fc6o7Qo3JW2aA%3D%3D;Domain=.caipiao.taobao.com;Path=/;Expires=Sat, 18-May-2019 08:45:44 GMT;","uc3=id2=VypTwv1vXUPq&vt3=F8dBy3qKU7lfemQzYHQ%3D&lg2=VFC%2FuZ9ayeYq2g%3D%3D&nk2=EFBZxtK4Kw%3D%3D;Domain=.taobao.com;Path=/;Expires=Mon, 10-Jun-2019 08:45:44 GMT;HttpOnly","uc1=cookie14=UoTZ48D5kKh8xA%3D%3D&cookie15=VFC%2FuZ9ayeYq2g%3D%3D&cookie21=UtASsssme%2BBq;Domain=.taobao.com;Path=/;Expires=Sat, 18-May-2019 08:45:44 GMT;","csg=90e619f0;Domain=.taobao.com;Path=/;Expires=Sat, 18-May-2019 08:45:44 GMT;","lgc=sn_baby;Domain=.taobao.com;Path=/;Expires=Mon, 10-Jun-2019 08:45:44 GMT;","t=442a42d1161c0a8620fe534283ceb5a8;Domain=.taobao.com;Path=/;Expires=Fri, 09-Aug-2019 08:45:44 GMT;","cookie17=VypTwv1vXUPq;Domain=.taobao.com;Path=/;Expires=Sat, 18-May-2019 08:45:44 GMT;HttpOnly","skt=8ef4770308e43bc0;Domain=.taobao.com;Path=/;Expires=Sat, 18-May-2019 08:45:44 GMT;HttpOnly","cookie2=3189d26e0391eaae9b679007ed912940;Domain=.taobao.com;Path=/;Expires=Sat, 18-May-2019 08:45:44 GMT;HttpOnly","uc4=nk4=0%40EolGnWPGn0GaP5tCkC95jF04&id4=0%40VX05qZjnlsjFk7XPWfOLKS03eMM%3D;Domain=.taobao.com;Path=/;Expires=Mon, 10-Jun-2019 08:45:44 GMT;HttpOnly","tracknick=sn_baby;Domain=.taobao.com;Path=/;Expires=Sun, 10-May-2020 08:45:44 GMT;","_cc_=Vq8l%2BKCLiw%3D%3D;Domain=.taobao.com;Path=/;Expires=Sun, 10-May-2020 08:45:44 GMT;","lid=;Domain=login.taobao.com;Path=/;Expires=Thu, 01-Jan-1970 00:00:00 GMT;","_l_g_=Ug%3D%3D;Domain=.taobao.com;Path=/;Expires=Sat, 18-May-2019 08:45:44 GMT;","sg=y66;Domain=.taobao.com;Path=/;Expires=Sat, 18-May-2019 08:45:44 GMT;","_nk_=sn_baby;Domain=.taobao.com;Path=/;Expires=Sat, 18-May-2019 08:45:44 GMT;","cookie1=AVNXwIRpXoAb1OPb4CDz2K8mXvrgRvJlKMPeMMEB%2FlI%3D;Domain=.taobao.com;Path=/;Expires=Sat, 18-May-2019 08:45:44 GMT;HttpOnly","_tb_token_=7eed15e86beea;Domain=.taobao.com;Path=/;Expires=Sat, 18-May-2019 08:45:44 GMT;"],"phone":"18502828078","userId":"463920786","sid":"3189d26e0391eaae9b679007ed912940","ecode":"VeqpN"},"ret":["SUCCESS::调用成功"],"v":"3.0"}'
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

