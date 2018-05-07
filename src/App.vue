<template>
  <div id="app">
    <tableComp :dataMain="dataMain"></tableComp>
  </div>
</template>

<script>
import jQuery from "jQuery";
import tableComp from "./components/tableComp.vue";

export default {
  name: "app",
  components: {
    tableComp
  },
  data: function() {
    return {
      dataMain: {
        Preferences: [],
      }
    };
  },
  methods: {
    parseResponse: function(xml) {
        var json = {
          Preferences: []
        };

        var preferences = xml.find("PreferenceJSON");

        for (var i = 0; i < preferences.length; i++) {
          var pref = jQuery(preferences[i]);
          json.Preferences.push({
            ControllerCode: pref.find("ControllerCode").html(),
            PreferenceCode: pref.find("PreferenceCode").html(),
            Name: pref.find("Name").html(),
            Description: pref.find("Description").html(),
            Status: pref.find("Status").html()
          });
        }

        return json;
    },
    getData: function() {

      var tableUrl = "http://test.eventdata.uk/API/MasterPerson/Preference.asmx/Load";

      var appVue = this;

      jQuery.ajax(tableUrl, {
        method: "POST",
        dataType: "xml",
        headers: {
          Authorization: "Basic RGF0YUNvbnRyb2xsZXI6MTIzNA=="
        },
        data: {
          ControllerCode: "TEST1"
        },
        success: function(response) {
            var xml = jQuery(response);

            appVue.dataMain = appVue.parseResponse(xml);
        },
        error: function(xhr, ajaxOptions, thrownError) {
          console.error(xhr.responseText);
          console.error(thrownError);
        }
      });
    }
  },
  mounted: function() {
    this.getData();
  }
};
</script>
