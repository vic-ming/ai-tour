<template>
  <div class="add-on-view">
    <div class="add-on-view-container container">
      <div class="add-on-view-title">{{ $t('addOn.title') }}</div>
      <table class="add-on-table">
        <thead>
          <tr>
            <th>{{ $t('addOn.tableHeaders.condition') }}</th>
            <th>{{ $t('addOn.tableHeaders.price') }}</th>
            <th>{{ $t('addOn.tableHeaders.discount') }}</th>
            <th>{{ $t('addOn.tableHeaders.note') }}</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in addOnData" :key="item.key">
            <td>{{ $t(`addOn.conditions.${item.key}`) }}</td>
            <td>{{ item.price }}</td>
            <td v-html="$t(`addOn.discounts.${item.discountKey}`)" ></td>
            <td>{{ $t(`addOn.notes.${item.noteKey}`) }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<script setup>
const addOnData = [
  {
    key: 'under1000',
    price: '1,000 NTD',
    discountKey: 'none',
    noteKey: 'small',
  },
  {
    key: 'over2000',
    price: '1,800 NTD',
    discountKey: 'percent10',
    noteKey: 'medium',
  },
  {
    key: 'over4000',
    price: '3,200 NTD',
    discountKey: 'percent20',
    noteKey: 'large',
  },
  {
    key: 'over8000',
    price: '5,600 NTD',
    discountKey: 'percent30',
    noteKey: 'best',
  },

]
</script>
<style lang="scss" scoped>
$primary-color: #353535;
.add-on-view {
  background-color: #F6F6F6;
  width: 100%;
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 60px 0;
  .add-on-view-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 20px;
    box-sizing: border-box;
    overflow: auto;
    .add-on-view-title {
      font-size: 20px;
      font-weight: 700;
      color: $primary-color;
      line-height: 1.5;
    }
  }
  .add-on-table {
    border-collapse: collapse;
    border-spacing: 0;
    overflow: hidden;
    color: $primary-color;
    line-height: 1.5;
    font-size: 16px;
    thead {
      background-color: #FAFAFA;
      border-bottom: 1px solid #f6f6f6;
      th {
        font-weight: 600;
      }
    }
    tr{
      height: 40px;
      td {
        background-color: #fff;
        box-sizing: border-box;
        border-bottom: 1px solid #EAEAEA;
        border-right: 1px solid #EAEAEA;
        &:nth-child(1), &:nth-child(2) {
          width: 120px;
          text-align: center;
        }
        &:nth-child(3) {
          width: 280px;
          text-align: center;
        }
        &:nth-child(4) {
          padding: 0 12px;
          width: 280px;
          text-align: left;
        }
        &:last-child {
          border-right: none;
        }

      }
    }

  }
}
</style>
