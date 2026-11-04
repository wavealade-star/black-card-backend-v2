
# BLACK CARD BACKEND - V2 - REAL PRODUCTION
Nigeria - NGN - No GitHub Drag & Drop Ready

## Features Included:
- Referral & Withdrawal UNLOCK only after membership approved (Backend enforces)
- Manual/Auto Withdrawal Toggle (Only one ON)
- Manual: Customer submits bank details -> appears in Admin -> Admin transfers via own bank app -> marks paid
- Auto: System transfers via Paystack/Flutterwave/Monnify
- Self-referral prevention, Email verification check, Transaction PIN, Wallet ledger append-only
- Extensibility: feature_flags, migrations, referral_rules, system_settings_history

## Deployment WITHOUT GitHub:
1. Download this folder black-card-backend as ZIP
2. Go to vercel.com -> Add New Project -> Browse -> Upload folder -> Deploy
3. In Vercel Settings -> Environment Variables -> Add:
   SUPABASE_URL = your Supabase Project URL
   SUPABASE_SERVICE_ROLE_KEY = your service_role key
   JWT_SECRET = any random long text
4. Deploy -> You get link https://black-card-backend.vercel.app

## API Endpoints (32 endpoints):
- POST /api/auth/register (with optional referral_code)
- POST /api/auth/login
- POST /api/auth/admin/login
- GET /api/memberships
- POST /api/purchases/create (enforces upgrade only)
- POST /api/purchases/:id/proof
- GET /api/purchases/my
- GET /api/admin/purchases/pending
- POST /api/admin/purchases/:id/approve (unlocks referral & withdrawal + triggers referral reward if qualified)
- POST /api/admin/purchases/:id/decline
- GET /api/wallet (shows eligibility flags)
- GET /api/system/withdrawal-mode
- POST /api/admin/settings/withdrawal-mode (toggle auto/manual, logs history, only one ON)
- POST /api/withdrawals/request (checks is_withdrawal_eligible, reserves funds, mode = current mode)
- GET /api/withdrawals/my
- GET /api/admin/withdrawals (shows bank details for manual transfer)
- POST /api/admin/withdrawals/:id/mark-paid (admin uploads proof after manual bank transfer)
- GET /api/referrals/my (checks is_referral_eligible, returns locked message if not eligible)
- GET /api/admin/users

## Real Business Rules Enforced by Backend (not frontend):
- Downgrade prohibited: Premium->Silver only upgrade
- Referral code locked until membership approved
- Withdrawal locked until membership approved
- Self-referral blocked at database level
- Wallet balance protected with reserve mechanism
- Append-only ledger - no silent delete
- All admin actions in audit_logs

## Selar Links Already Configured:
Premium ₦600: https://selar.com/982956ul1r
Silver ₦1500: https://selar.com/p5c5o115a1
Gold ₦2500: https://selar.com/r01h1w0kb1
Diamond ₦5000: https://selar.com/5332825453
