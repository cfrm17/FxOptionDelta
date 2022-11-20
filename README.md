# FX Option Delta

The pricing of a vanilla European option is done using the following original (market) input: spot
FX rate, time to expiry, strike, domestic foreign interest rate, foreign interest rate, and volatility
extracted from smile using all prior five parameters.

 If we want a scenario price where we assume a different spot FX, then the ingredients for pricing the new scenario option will be: new spot FX, time to expiry (as original), strike (as original), domestic foreign interest rate (as original), foreign interest rate (as original), and volatility extracted from smile using all these five parameters (this volatility will clearly be different from the volatility extracted in the original case as in the extraction process we are using a different spot FX rate).

Full Delta is computed by finite differencing using scenario price (see https://finpricing.com/lib/FiZeroBond.html ) for spot FX rate shifted up and scenario price for spot FX rate shifted down (the shift in this case is infinitesimal). Even though methodologically different, these two deltas should be relatively close.

Let be the spot FX rate of a currency pair FOREIGN/DOMESTIC (FOR/DOM, f/d) at time t. In the FOR/DOM notation scheme, when one considers, for example, the EUR/USD-spot trading, say, at 1.22 USD per 1 EUR, the currency USD is used to measure 1 EUR, therefore we say that EUR is the underlying (the asset, the foreign currency, the base currency) and USD is the numeraire (the domestic currency, the quote currency) used to value the asset 1 EUR. t S

Let denote the domestic interest rate, the foreign interest rate, and σ d r f r the volatility parameter. The following continuous geometric Brownian process (under risk-neutral measure) usually models the spot FX rate (here is the standard Brownian motion):

 

Let 0 be current time, and T be a fixed expiry date (in this theoretical presentation we will ignore the spot time lag, but not in our concrete examples). The payoff of a vanilla European call (put) option on the spot FX rate having notional unit of foreign currency, expiry T and strike rate K is NFOR* max(S K,0) (NFOR T ⋅ − max( ,0) FOR T N ⋅ K − S ). We will use the flag β = 1 for call (also C letter), and β = −1 for put (also P letter). The payoff can be presented as follows:

 

From now on we consider , as the continuously compounded zero rates applying to the time period [0,T] (they are usually derived from deposit rates only). d r f rF E[S S S] T = = 0 | 

Let F be the forward FX rate (forward price of the underlying), that is , were S will denote the known spot FX rate at 0. By interest rate parity no-arbitrage argument, we must have:

 

FX markets quote forward point quantity Q := F – S for maturity T , and when is given, then

 

Under Black-Scholes assumptions, of which the most important one is constant volatility of the
underlying (parameterσ is constant), the value (price) of a vanilla European option is:

 

where σ and Φ stands for the cumulative distribution function of the standard normal random variable, that is 

 

In practice we must consider the available market volatility smile (whose existence is inconsistent with BS assumptions). From the smile, using the procedure, we extract the volatility to be inputted in the BS calculator above (accounting for moneyness K), that is:

So the option value can be written as:

 

The Full Delta is then computed from independent re-pricing for shifted spot rates and accordingly computed volatilities:

Direct Quote Full Delta (EURUSD):

 

where , and . The shock is pair dependent. In the EURUSD direct quote Atlas case,
S + = S +ε S − = S −ε
ε = 0.00005USD . Notice that the difference between Atlas direct quote delta and theoretical right delta described above is a factor of KF. The DOM (that is, USD in direct quote EURUSD) delta-hedge in Atlas is then the above Atlas delta multiplied by the number above. N K FOR ⋅

Indirect Quote Full Delta (JPYUSD):

 
