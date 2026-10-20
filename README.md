# Mortgage Prepayment Calculator

A single-page calculator for annuity mortgages. It shows what a one-off early repayment does to your loan: either a lower monthly payment or a shorter term.

Available in English and Lithuanian, with light and dark themes.

## Features

- **Two repayment strategies**
  - **A · Lower monthly payment:** keeps the remaining term and recalculates the payment.
  - **B · Shorter loan term:** keeps the payment and works out how many months you save.
- **Side-by-side comparison** of both strategies: interest saved, new payment, new term and end date.
- **Payment breakdown:** the interest and principal parts of the next payment, before and after the prepayment.
- **Flexible term input:** months, years, or the exact final payment date.
- **Interest day count**
  - **Rate ÷ 12:** the textbook method, with equal months.
  - **Actual/360:** interest for the real number of days in each payment period. Many European banks use this. With an end date set, the result matches a bank schedule to within a cent or so.
- **Real-time results** as you type, with inputs remembered in the browser.
- **Currencies:** EUR, DKK, GBP and USD.

## How it calculates

The monthly payment is a standard annuity:

```
Payment = P × r / (1 − (1 + r)^−n)
```

- `P` is the remaining principal.
- `n` is the number of remaining payments.
- `r` is the rate per payment period.

With **Actual/360** and an end date, the calculator lists every payment date from your most recent payment to the end date. It charges interest for the actual days in each period and finds the level payment that clears the balance on the final date.

**Assumptions**
- A fixed interest rate for the rest of the loan.
- No early repayment fees.
- The prepayment is made on your latest payment date.

Check your loan agreement for the day-count method and any fees your bank charges.

## Running locally

There's no build step. Open `index.html` in a browser, or serve the folder:

```bash
npx serve .
```

## Deploying

It's a static site, so any static host works. On Vercel:

```bash
npx vercel          # preview deployment
npx vercel --prod   # production
```

Or import the GitHub repo on vercel.com with the **Other** framework preset and no build command.

## Tech

- Plain HTML and JavaScript in a single `index.html`.
- [Tailwind CSS](https://tailwindcss.com) via the Play CDN, and [Google Fonts](https://fonts.google.com) (Schibsted Grotesk, IBM Plex Mono).
- No tracking, and no data leaves the browser. Inputs and preferences are kept in `localStorage`.

## Disclaimer

The results are estimates for planning. Your bank's figures may differ by a few cents because of rounding, and by more if fees, rate changes or other contract terms apply.
