<template>
    <div>
        Number of participants: {{returnObject.noOfParticipants}}
    </div>
    <div>
        Max Price: {{returnObject.maxPrice}}
    </div>
    <div>
        Type: {{returnObject.type}}
    </div>
    <div>
        Data: {{data.data}}
    </div>
</template>

<script>
export default {
  name: "DisplayResult",
  props: {
    returnObject: Object,
    data: Object
  },
};
</script>