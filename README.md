# Frontend Setup Guide

## Prerequisites

- Node.js 18+
- npm or yarn

## Installation

### 1. Install Dependencies

```bash
npm install
```

### 2. Configure Environment Variables

Create `.env.local` file from `.env.local.example`:

```bash
cp .env.local.example .env.local
```

## Running the Application

### Development

```bash
npm run dev
```

Application runs on `http://localhost:3000` soon

### Production Build

```bash
npm run build
npm start
```

### Lint Code

```bash
npm run lint
```

## Project Structure

```
src/
├── app/              - Next.js pages and layouts
│   ├── auth/        - Authentication pages
│   ├── marketplace/ - Product listing
│   ├── seller/      - Seller dashboard
│   ├── admin/       - Admin dashboard
│   ├── customer/    - Customer pages
│   └── page.tsx     - Home page
├── components/      - Reusable React components
│   └── Navbar.tsx   - Navigation bar
├── services/        - API services
│   └── api.ts       - Axios API client
├── store/           - Zustand state management
├── types/           - TypeScript interfaces
├── lib/             - Utility functions
└── styles/          - Global styles
```

## Key Features

### Pages

#### Home (`/`)
- Landing page with CTAs
- Features overview
- Getting started guide

#### Authentication
- `/register` - User registration
- `/login` - User login
- Role selection (Customer/Seller)

#### Marketplace (`/marketplace`)
- Product listing with filters
- Search functionality
- Price range filters
- Sort options (newest, popular, price)

#### Seller Dashboard (`/seller/dashboard`)
- Product management
- Order tracking
- Sales statistics
- Add new product

#### Admin Dashboard (`/admin/dashboard`)
- System statistics
- User management
- CSV export functionality
- Order management

#### Customer Features
- Wishlist management
- Product reviews
- Order history
- Recently viewed products

### Components

#### Navbar
- Navigation menu
- User profile
- Dark mode toggle
- Mobile responsive

### State Management

Using Zustand for:
- User authentication state
- UI preferences (dark mode)
- Global state

### API Integration

Axios client configured with:
- Base URL from environment
- Automatic token injection
- Error handling
- Request/response interceptors

## Styling

### Tailwind CSS
- Utility-first CSS framework
- Dark mode support
- Responsive design

### ShadCN UI
- Pre-built accessible components
- Customizable design system
- Radix UI primitives

## Dark Mode

Features:
- Auto-detection of system preference
- Manual toggle in navbar
- Persistent preference in localStorage
- Smooth transitions

## Responsive Design

Breakpoints:
- Mobile: < 640px
- Tablet: 640px - 1024px
- Desktop: > 1024px

## Environment Variables

```
NEXT_PUBLIC_API_URL    - Backend API base URL
NEXT_PUBLIC_RAZORPAY_KEY - Razorpay public key
```

## Testing

### Build Check
```bash
npm run build
```

### Lint Check
```bash
npm run lint
```

## Common Tasks

### Add New Page

1. Create file in `src/app/[name]/page.tsx`
2. Use client/server component as needed
3. Import components and services
4. Add styling with Tailwind

### Add New Component

1. Create file in `src/components/[Name].tsx`
2. Export default component
3. Use in pages

### Call API

```typescript
import { productService } from '@/services/api';

const response = await productService.getMarketplaceProducts({
  search: 'laptop',
  sort: 'price-low'
});
```

### Use Global State

```typescript
import { useAuthStore } from '@/store';

const { user, setUser, logout } = useAuthStore();
```

### Show Toast Notification

```typescript
import toast from 'react-hot-toast';

toast.success('Product added!');
toast.error('Something went wrong');
```

## Optimization

### Image Optimization
- Using Next.js Image component
- Automatic format conversion
- Responsive image loading
- Cloudinary CDN integration

### Code Splitting
- Automatic route-based code splitting
- Dynamic imports for heavy components
- Lazy loading of components

### Performance
- Next.js built-in optimizations
- CSS compression
- JavaScript minification
- Static generation where possible

## Deployment

### Vercel (Recommended)

1. Push to GitHub
2. Connect repository to Vercel
3. Add environment variables
4. Deploy

```bash
vercel
```

### Docker

```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY . .
RUN npm install
RUN npm run build
EXPOSE 3000
CMD ["npm", "start"]
```

### Manual Deployment

```bash
npm run build
npm start
```

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## Troubleshooting

### API Connection Error
- Check backend is running
- Verify API_URL environment variable
- Check CORS configuration

### Build Errors
- Clear `.next` folder: `rm -rf .next`
- Clear node_modules: `rm -rf node_modules && npm install`
- Check TypeScript errors: `npm run lint`

### Dark Mode Not Working
- Clear localStorage
- Check localStorage permissions
- Verify Tailwind config

## Performance Tips

- Use Image component for images
- Implement pagination for lists
- Use React.memo for expensive components
- Lazy load heavy components
- Optimize dependencies

## Production Checklist

- [ ] Environment variables configured
- [ ] API endpoints verified
- [ ] Build succeeds
- [ ] No console errors
- [ ] Mobile responsive
- [ ] Dark mode working
- [ ] Auth flow tested
- [ ] All pages accessible
- [ ] Performance optimized
- [ ] Error boundaries added

## Support

For issues:
1. Check browser console for errors
2. Check network tab in DevTools
3. Verify environment variables
4. Check backend API status
5. Clear browser cache

## Resources

- [Next.js Documentation](https://nextjs.org/docs)
- [Tailwind CSS](https://tailwindcss.com)
- [ShadCN UI](https://ui.shadcn.com)
- [Zustand](https://github.com/pmndrs/zustand)

## License

Copyright © 2026 Riya Uppal. All Rights Reserved.

This project and its source code are proprietary and confidential.

No part of this project, including but not limited to the source code, UI/UX design, database schema, documentation, branding, business logic, or associated assets, may be copied, modified, distributed, reproduced, reverse-engineered, sold, or used for commercial or academic purposes without prior written permission from the author.

Unauthorized use, reproduction, or distribution of this software is strictly prohibited.


Proprietary software. All rights reserved.
