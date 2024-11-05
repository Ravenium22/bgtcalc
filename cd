class BGTCalculator {
  constructor() {
    this.tvl = 0;
    this.stakedPercentage = 0;
    this.userSharePercentage = 0;
    this.yearlyBGTDistribution = 0;
    this.gaugeCaptureRate = 0;
  }

  getUserInputs() {
    console.log("\n=== BGT Rewards Calculator ===\n");

    this.tvl = parseFloat(prompt("Enter HONEY-USDC TVL (in USD):"));
    this.stakedPercentage = parseFloat(prompt("Enter Staked in Gauge Vault percentage (e.g., 32.89):"));
    this.userSharePercentage = parseFloat(prompt("Enter your total shares percentage (e.g., 0.50):"));
    this.yearlyBGTDistribution = parseFloat(prompt("Enter estimated yearly BGT distribution:"));
    this.gaugeCaptureRate = parseFloat(prompt("Enter HONEY-USDC Gauge Vault BGT Capture rate percentage (e.g., 18):"));
  }

  calculateRewards() {
    // Calculate total value staked in gauge
    const totalStaked = this.tvl * (this.stakedPercentage / 100);

    // Calculate user's share in USD
    const userShareUSD = totalStaked * (this.userSharePercentage / 100);

    // Calculate yearly BGT distribution for HONEY-USDC
    const yearlyHoneyUSDCBGT = this.yearlyBGTDistribution * (this.gaugeCaptureRate / 100);

    // Calculate estimated BGT rate per year
    const estimatedBGTYear = (yearlyHoneyUSDCBGT * userShareUSD) / totalStaked;

    // Calculate daily BGT rate
    const estimatedBGTDay = estimatedBGTYear / 365;

    return {
      totalStaked: totalStaked,
      userShareUSD: userShareUSD,
      yearlyHoneyUSDCBGT: yearlyHoneyUSDCBGT,
      estimatedBGTYear: estimatedBGTYear,
      estimatedBGTDay: estimatedBGTDay,
    };
  }

  displayResults(results) {
    console.log("\n=== Results ===\n");
    console.log(`Total value Staked in Gauge: $${results.totalStaked.toFixed(2)}`);
    console.log(`Your total shares in USD: $${results.userShareUSD.toFixed(2)}`);
    console.log(`Yearly BGT Distribution for HONEY-USDC: ${results.yearlyHoneyUSDCBGT.toFixed(2)} BGT`);
    console.log(`Estimated BGT rate per year: ${results.estimatedBGTYear.toFixed(2)} BGT`);
    console.log(`Estimated BGT rate per day: ${results.estimatedBGTDay.toFixed(2)} BGT`);

    // Calculate and display multiplier
    const currentDaily = 1000; // Current daily BGT earning
    const multiplier = currentDaily / results.estimatedBGTDay;
    console.log(`\nMultiplier (based on 1000 BGT daily earning): ${multiplier.toFixed(2)}x`);
  }
}

function main() {
  const calculator = new BGTCalculator();
  calculator.getUserInputs();
  const results = calculator.calculateRewards();
  calculator.displayResults(results);
}

main();
