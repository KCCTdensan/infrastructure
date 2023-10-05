# argo-cd

`argo/argo-cd`は素の状態だと`default`名前空間を使うので，それを変更する為に値を弄る

fishではこうやる:

```fish
for crd in "applications.argoproj.io" "applicationsets.argoproj.io" "appprojects.argoproj.io"
  kubectl annotate --overwrite crd $crd meta.helm.sh/release-namespace=argo-cd
end
helm install --create-namespace -n argo-cd argo-cd argo/argo-cd
```
