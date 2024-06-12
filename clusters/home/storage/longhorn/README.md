We need to set longhorn tag:
```
kubectl annotate node rpi-0 node.longhorn.io/default-node-tags='["persistent"]'
```
