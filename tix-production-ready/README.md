# TIX Design Redesign — Clone من v0-tix-eg-clone.vercel.app

## الملفات المُنشأة

```
src/
├── styles/
│   └── tix-design.css              ← نظام التصميم الكامل (CSS Variables + كل الـ classes)
├── component/
│   ├── Navbar/
│   │   └── Navbar.jsx              ← شريط التنقل (logo + search + cart + categories)
│   ├── Footer/
│   │   └── Footer.jsx              ← الـ footer (brand + links + social + language)
│   └── ProductCard/
│       └── ProductCard.jsx         ← كارد المنتج (يُستخدم في كل مكان)
└── pages/
    ├── Home/
    │   └── Home.jsx                ← الصفحة الرئيسية (hero + منتجات)
    ├── ProductsDetalis/
    │   └── ProductsDetalis.jsx     ← صفحة تفاصيل المنتج (كاملة)
    ├── Cart/
    │   └── Cart.jsx                ← صفحة السلة
    ├── Login/
    │   └── Login.jsx               ← صفحة تسجيل الدخول
    └── Register/
        └── Register.jsx            ← صفحة التسجيل
```

---

## خطوات التطبيق

### 1. انسخ مجلد `styles/`
```
src/styles/tix-design.css
```
هذا الملف هو الأساس — يحتوي على كل الـ CSS Variables والـ classes.

### 2. استبدل الـ Components والـ Pages
استبدل الملفات القديمة بالملفات الجديدة (نفس المسارات).

### 3. أضف Cairo font في `public/index.html`
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
```

### 4. استبدل استيراد الـ CSS في `App.css` أو `index.css`
```css
/* احذف كل CSS القديم وخلي فقط: */
@import './styles/tix-design.css';
```

### 5. عدّل `App.js` أو `AppRoutes.jsx` لإضافة الصفحات الجديدة
```jsx
import Navbar from './component/Navbar/Navbar';
import Footer from './component/Footer/Footer';
import Home from './pages/Home/Home';
import Cart from './pages/Cart/Cart';
import Login from './pages/Login/Login';
import Register from './pages/Register/Register';

// في الـ layout الرئيسي:
<Navbar cartLength={cartLength} />
<Routes>
  <Route path="/" element={<Home setFavlength={setFavlength} />} />
  <Route path="/product/:id" element={<ProductsDetalis setFavlength={setFavlength} />} />
  <Route path="/cart" element={<Cart />} />
  <Route path="/login" element={<Login />} />
  <Route path="/register" element={<Register />} />
</Routes>
<Footer />
```

---

## التصميم — مطابق حرفياً للـ v0

| العنصر | القيمة |
|--------|--------|
| اللون الأساسي | `#f97316` (برتقالي) |
| الخط | Cairo (Google Fonts) |
| الاتجاه | RTL |
| الـ Border Radius | 12px للكروت |
| Shadow | `0 2px 12px rgba(0,0,0,0.08)` |

---

## ملاحظات مهمة
- `AppRoutes.jsx` لا تُعدَّل — فقط أضف الاستيرادات
- كل الـ API calls تستخدم `REACT_APP_API_BASE_URL` من `.env`
- الـ auth token يُقرأ من `localStorage.getItem("token")`
- دعم كامل للغتين (ar/en) عبر `i18n.language`
