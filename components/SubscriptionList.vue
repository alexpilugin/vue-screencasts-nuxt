<template>
  <div>
    <span v-for="plan in plans" :key="plan.id">
      <slot :plan="plan" />
    </span>
  </div>
</template>

<script>
  import subscriptionPlanJson from '@/utils/subscription-plan-data.json';
  export default {
    data(){
      let plans = subscriptionPlanJson.plans;
      let env = this.$root.context.env.stripeEnv;
      console.log(plans, env, this.$root.context)
      return {
        plans: plans.filter(p => p.env == env && !p.deprecated)
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>