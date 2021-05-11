<template>
  <div>
    <link rel="stylesheet" type="text/css" href="potree/potree.css" />

    <div
      class="potree_container"
      style="position: absolute; width: 100%; height: 100%; left: 0px; top: 0px"
    >
      <div id="potree_render_area" ref="renderArea"></div>
    </div>
  </div>
</template>

<script>
/*global viewer, Potree*/
const loadCloud = () => {
  Potree.loadPointCloud(
    "pointclouds/maps-class-test-12.laz_converted/metadata.json",
    "n0",
    (e) => {
      let scene = viewer.scene;
      let pointcloud = e.pointcloud;

      let material = pointcloud.material;
      material.size = 2;
      material.pointSizeType = Potree.PointSizeType.FIXED;
      material.shape = Potree.PointShape.CIRCLE;
      material.activeAttributeName = "classification";
      material.opacity = 0.17;

      let classification = {
        DEFAULT: { visible: true, name: "default", color: [1, 1, 1, 1] },
      };

      viewer.setClassifications(classification);

      console.log(material.classification);

      scene.addPointCloud(pointcloud);

      viewer.fitToScreen();

      document.querySelector("canvas").style.removeProperty("position");
    }
  );
};
const addPotreeLib = (renderArea) => {
  let pScript = document.createElement("script");
  pScript.setAttribute("src", "potree/potree.full.js");
  document.head.appendChild(pScript);

  pScript.onload = () => {
    window.viewer = new Potree.Viewer(renderArea);

    viewer.setEDLEnabled(false);
    viewer.setFOV(60);
    viewer.setPointBudget(1000000);
    viewer.loadSettingsFromURL();
    viewer.setBackground("black");

    console.log("Initialized Potree");

    loadCloud();
  };
};

export default {
  mounted() {
    addPotreeLib(this.$refs.renderArea);
  },
};
</script>
