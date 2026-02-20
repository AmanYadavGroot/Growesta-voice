# Growesta Voice SaaS MVP

A comprehensive Spanish voice bot platform for small and medium-sized businesses (salons, clinics, restaurants, logistics, HR, etc.).

## 🚀 Features

### Core Functionality
- **Multi-tenant System**: Each business has isolated data and configuration
- **Voice Bot Templates**: Pre-built templates for Bookings, Orders, Interviews, and Screening
- **Real-time Call Management**: Inbound/outbound Spanish calls with Twilio integration
- **Automatic Transcriptions**: Convert conversations to text for analysis
- **Smart Ranking Algorithm**: Non-AI ranking system based on:
  - Keyword presence (50 pts)
  - Duration window (20 pts) 
  - Completeness (20 pts)
  - Positive/negative words (10 pts)
- **Comprehensive Dashboard**: Call logs, transcripts, rankings, and settings
- **Stripe Billing**: Subscription management with webhooks
- **Admin Dashboard**: Usage monitoring, error logs, tenant management

### Voice Bot Types
1. **Booking Bot**: Automates appointment scheduling for salons and clinics
2. **Order Bot**: Handles food orders for restaurants
3. **Interview Bot**: Conducts phone interviews for HR teams
4. **Screening Bot**: Evaluates candidates with structured questions

## 🛠 Tech Stack


### Frontend
- **React 19** with Next.js 15
- **Tailwind CSS** for styling
- **Radix UI** components
- **TypeScript** for type safety
- **Axios** for API calls

### Backend
- **Node.js** with Express.js
- **PostgreSQL** database with Sequelize ORM
- **JWT** authentication
- **Twilio** for voice calls and transcriptions
- **Stripe** for billing and subscriptions

### Hosting
- **Vercel** for frontend deployment
- **Render** for backend deployment

## 📋 Prerequisites

- Node.js 18+ 
- PostgreSQL 14+
- Twilio account with phone number
- Stripe account for billing
- Git

## 🚀 Quick Start

### 1. Clone the Repository
```bash
git clone <repository-url>
cd growesta-voice-development
```

### 2. Backend Setup

```bash
cd backend
npm install
```

Create a `.env` file in the backend directory:
```env
# Database
DATABASE_URL=postgres://username:password@localhost:5432/growesta_voice

# JWT
JWT_SECRET=your-super-secret-jwt-key-here

# Twilio
TWILIO_ACCOUNT_SID=your-twilio-account-sid
TWILIO_AUTH_TOKEN=your-twilio-auth-token
TWILIO_WEBHOOK_URL=https://your-domain.com/api/twilio

# Stripe
STRIPE_SECRET_KEY=sk_test_your-stripe-secret-key
STRIPE_WEBHOOK_SECRET=whsec_your-webhook-secret
STRIPE_BASIC_PRICE_ID=price_your-basic-price-id
STRIPE_PROFESSIONAL_PRICE_ID=price_your-professional-price-id
STRIPE_ENTERPRISE_PRICE_ID=price_your-enterprise-price-id

# Application
NODE_ENV=development
PORT=3001
FRONTEND_URL=http://localhost:3000
BASE_URL=https://your-domain.com
```

### 3. Database Setup

Create a PostgreSQL database:
```sql
CREATE DATABASE growesta_voice;
```

The application will automatically create tables on first run.

### 4. Frontend Setup

```bash
cd .. # Back to root directory
npm install
```

Create a `.env.local` file in the root directory:
```env
NEXT_PUBLIC_API_URL=http://localhost:3001/api
```

### 5. Run the Application

Start the backend:
```bash
cd backend
npm run dev
```

Start the frontend (in a new terminal):
```bash
npm run dev
```

Visit `http://localhost:3000` to see the application.

## 🔧 Configuration

### Twilio Setup
1. Create a Twilio account
2. Purchase a phone number
3. Configure webhooks to point to your backend
4. Update environment variables

### Stripe Setup
1. Create a Stripe account
2. Create products and prices for your subscription plans
3. Configure webhooks for subscription events
4. Update environment variables

### Voice Bot Configuration
Each voice bot can be customized with:
- Business name and information
- Service offerings
- Business hours
- Voice type and language
- Custom prompts and responses

## 📊 Subscription Plans

### Free Plan
- 100 calls per month
- 1 active voice bot
- Basic transcriptions
- Email support

### Basic Plan - $299 MXN/month
- 500 calls per month
- 3 active voice bots
- Complete transcriptions
- Basic analytics
- Priority support

### Professional Plan - $799 MXN/month
- 2,000 calls per month
- 10 active voice bots
- Advanced transcriptions
- Complete analytics
- Automatic rankings
- 24/7 support

### Enterprise Plan - $1,999 MXN/month
- 10,000 calls per month
- 50 active voice bots
- Unlimited transcriptions
- Advanced analytics
- Custom rankings
- Dedicated support
- Custom API

## 🎯 Performance Targets

- **10 concurrent calls** stable performance
- **15 concurrent calls** best effort
- **~3 minutes** average call duration
- **Real-time** transcription processing
- **Multi-tenant** data isolation

## 🔐 Security Features

- JWT-based authentication
- Multi-tenant data isolation
- Role-based access control
- Secure webhook validation
- Environment variable protection

## 📱 API Endpoints

### Authentication
- `POST /api/auth/register` - Register new business
- `POST /api/auth/login` - User login
- `GET /api/auth/profile` - Get user profile
- `PUT /api/auth/profile` - Update profile
- `PUT /api/auth/change-password` - Change password

### Voice Bots
- `GET /api/voiceBots` - List voice bots
- `POST /api/voiceBots` - Create voice bot
- `PUT /api/voiceBots/:id` - Update voice bot
- `DELETE /api/voiceBots/:id` - Delete voice bot
- `GET /api/voiceBots/templates/list` - Get templates

### Calls
- `GET /api/calls` - List calls
- `POST /api/calls/make-call` - Make outbound call
- `GET /api/calls/stats/overview` - Call statistics
- `GET /api/calls/stats/rankings` - Call rankings

### Billing
- `GET /api/billing/plans` - Get subscription plans
- `POST /api/billing/checkout` - Create checkout session
- `POST /api/billing/portal` - Create customer portal
- `POST /api/billing/cancel` - Cancel subscription

### Twilio Webhooks
- `POST /api/twilio/incoming` - Handle incoming calls
- `POST /api/twilio/call-status` - Call status updates
- `POST /api/twilio/recording-status` - Recording processing

## 🚀 Deployment

### Frontend (Vercel)
1. Connect your GitHub repository to Vercel
2. Set environment variables in Vercel dashboard
3. Deploy automatically on push to main branch

### Backend (Render)
1. Connect your GitHub repository to Render
2. Set environment variables in Render dashboard
3. Configure PostgreSQL database
4. Deploy automatically on push to main branch

### Environment Variables for Production
Update the following for production:
- `NODE_ENV=production`
- `FRONTEND_URL=https://your-domain.vercel.app`
- `BASE_URL=https://your-backend.onrender.com`
- `TWILIO_WEBHOOK_URL=https://your-backend.onrender.com/api/twilio`
- Use production Stripe keys
- Use production Twilio credentials

## 🧪 Testing

### Demo Credentials
- **Email**: demo@growesta.com
- **Password**: demo123

### Test Phone Numbers
Use Twilio test phone numbers for development:
- `+15005550006` - Valid number
- `+15005550001` - Invalid number

## 📈 Monitoring

### Admin Dashboard Features
- Business usage monitoring
- Error log tracking
- Tenant management (pause/delete)
- System performance metrics
- Subscription status overview

### Key Metrics
- Total calls processed
- Success rates by bot type
- Average call duration
- Ranking distribution
- Subscription conversion rates

## 🤝 Support

For technical support or questions:
- Email: support@growesta.com
- Documentation: [Link to docs]
- Issues: [GitHub Issues]

## 📄 License

This project is proprietary software. All rights reserved.

## 🎉 Success Criteria

✅ **Multi-tenant system** with isolated data  
✅ **Voice bot templates** for all business types  
✅ **Real-time call processing** with Twilio  
✅ **Automatic transcriptions** and rankings  
✅ **Stripe billing integration** with webhooks  
✅ **Comprehensive dashboard** for all features  
✅ **Admin panel** for tenant management  
✅ **Production-ready deployment** on Vercel/Render  

---

**Growesta Voice SaaS MVP** - Delivering intelligent voice automation for SMBs in 14 days or less.