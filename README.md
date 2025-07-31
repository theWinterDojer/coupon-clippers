# Digital Coupon Clippers

Automated JavaScript bookmarklets for clipping digital coupons from CVS and Publix websites.

## ⚡ Quick Start

1. **Copy the bookmarklet code** for your desired store
2. **Create a new bookmark** in your browser
3. **Paste the code** as the bookmark URL
4. **Navigate** to the store's coupon page
5. **Click the bookmark** to start clipping!

## 🏪 Supported Stores

### CVS Pharmacy
- **File**: `cvs.txt`
- **Page**: Navigate to CVS ExtraCare coupons page
- **Features**: Automatic scrolling, infinite scroll detection, smart termination

### Publix
- **File**: `publix.txt` 
- **Page**: Navigate to Publix digital coupons page
- **Features**: Load more button automation, advanced bot detection bypass

## 📋 Installation Instructions

### Method 1: Manual Bookmark Creation
1. **Copy the entire code** from the appropriate `.txt` file
2. **Right-click your bookmarks bar** → "Add page" or "Add bookmark"
3. **Name**: Enter "CVS Clipper" or "Publix Clipper"
4. **URL**: Paste the copied JavaScript code (starting with `javascript:`)
5. **Save the bookmark**

### Method 2: Drag & Drop (if supported)
Some browsers allow dragging these links directly to your bookmarks bar:

**CVS Clipper**: [📎 Add CVS Clipper](javascript:(async()=>{const delay=ms=>new Promise(r=>setTimeout(r,ms)),scrollDelay=1000,clipDelay=800;let clipped=0,scrollCount=0;const isAtBottom=()=>(window.innerHeight+window.scrollY)>=document.body.offsetHeight-100;console.log("📜 CVS Clipper started...");while(!isAtBottom()&&scrollCount<50){let coupons=[...document.querySelectorAll("button.coupon-action.button-blue.sc-send-to-card-action")];for(let btn of coupons){if(btn.offsetParent!==null&&!btn.disabled){try{btn.scrollIntoView({behavior:"smooth",block:"center"});btn.click();clipped++;console.log(`🔘 Clipped #${clipped}`);await delay(clipDelay);}catch(e){console.warn("⚠️ Clip failed:",e);}}}scrollCount++;window.scrollBy(0,500);await delay(scrollDelay);console.log(`📍 Scroll ${scrollCount}, at bottom: ${isAtBottom()}`);}console.log(`🎉 Done! Clipped ${clipped} coupons.`);alert(`🎉 Done!\nYou clipped ${clipped} new coupon${clipped===1?"":"s"}.`);})())

*Note: Drag & drop method may not work in all browsers. Use Manual method if links don't work.*

## 🎯 How to Use

1. **Navigate** to the store's digital coupon page
2. **Click your bookmarklet** in the bookmarks bar
3. **Watch the automation** run (check browser console for progress)
4. **Wait for completion** alert showing total coupons clipped

## ⚙️ Features

- **Smart Detection**: Identifies unclipped coupons automatically
- **Error Handling**: Graceful failure recovery
- **Progress Tracking**: Console logging and completion alerts  
- **Bot Detection Bypass**: Advanced human-like interaction simulation
- **Responsive Design**: Works across different screen sizes

## 🔧 Troubleshooting

### Common Issues
- **"Script not working"**: Ensure you're on the correct coupon page
- **"No coupons found"**: All coupons may already be clipped
- **"Bookmark not clickable"**: Verify the JavaScript code starts with `javascript:`

### Browser Compatibility
- ✅ Chrome/Chromium browsers
- ✅ Firefox
- ✅ Safari
- ✅ Edge

## ⚠️ Legal Disclaimer

These bookmarklets are provided for educational and personal use only. Users are responsible for:

- Ensuring compliance with store Terms of Service
- Respecting website usage policies  
- Using automation responsibly and ethically
- Understanding that automation may violate some site terms

**Use at your own discretion and risk.**

## 🤝 Contributing

Found a bug or want to improve the clippers?

1. Fork this repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Commit your changes (`git commit -am 'Add improvement'`)
4. Push to the branch (`git push origin feature/improvement`)
5. Create a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔄 Updates

Check back regularly for updates as stores may change their website structure, requiring bookmarklet updates.

---

**⭐ Star this repo if it saves you time clipping coupons!**