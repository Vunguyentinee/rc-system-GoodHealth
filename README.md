# rc-system-GoodHealth

## Required environment variables

The app no longer ships with hardcoded database or JWT secrets. Set these before running locally or deploying (e.g. in Render's dashboard under Environment):

| Variable | Description | Example |
|---|---|---|
| `DB_URL` | JDBC URL for the Postgres database | `jdbc:postgresql://<host>/<db>?sslmode=require` |
| `DB_USERNAME` | Database username | `neondb_owner` |
| `DB_PASSWORD` | Database password | *(secret)* |
| `JWT_SECRET` | HMAC-SHA256 signing key for JWTs, at least 32 bytes | *(generate a random 32+ byte string, e.g. `openssl rand -base64 48`)* |
| `JWT_EXPIRATION_MS` | Optional, token lifetime in ms | `86400000` (default) |

The AI recommendation service (`ai_service/`) additionally requires:

| Variable | Description |
|---|---|
| `DATABASE_URL` | SQLAlchemy-style Postgres URL, e.g. `postgresql://user:pass@host/db?sslmode=require` |

**If you previously ran this app with the credentials that used to be committed to this repo, rotate them now** (Neon DB password and generate a fresh `JWT_SECRET`) — anything committed to git history should be treated as compromised even after being removed.
