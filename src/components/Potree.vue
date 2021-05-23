<template>
  <div>
    <link
      rel="stylesheet"
      type="text/css"
      href="/assets/js/potree/potree.css"
    />

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
const loadCloud = (pointcloud) => {
  Potree.loadPointCloud(pointcloud, "n0", (e) => {
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

    for (let i = 0; i < 27; i++) {
      classification[i] = {
        visible: true,
        name: "default",
        color: [1, 1, 1, 1],
      };
    }

    viewer.setClassifications(classification);

    console.log(classification);

    scene.addPointCloud(pointcloud);

    viewer.fitToScreen();
  });
};
const addPotreeLib = (renderArea, pointcloud) => {
  let pScript = document.createElement("script");
  pScript.setAttribute("src", `/assets/js/potree/potree.full.js`);
  document.head.appendChild(pScript);

  pScript.onload = () => {
    window.viewer = new Potree.Viewer(renderArea);

    viewer.setEDLEnabled(false);
    viewer.setFOV(60);
    viewer.setPointBudget(1000000);
    viewer.loadSettingsFromURL();
    viewer.setBackground("black");

    console.log("Initialized Potree");

    loadCloud(pointcloud);
  };
};

export default {
  props: {
    pointcloud: String,
  },
  mounted() {
    addPotreeLib(this.$refs.renderArea, this.pointcloud);
  },
};
</script>
