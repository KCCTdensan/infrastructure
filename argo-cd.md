# argo-cd

`argo/argo-cd`は素の状態だと`default`名前空間を使うので，それを変更する為に値を弄る

fishではこうやる:

```fish
helm repo update
helm repo add argo https://argoproj.github.io/argo-helm
helm upgrade -i --create-namespace -n argo-cd argo-cd argo/argo-cd
for crd in "applications.argoproj.io" "applicationsets.argoproj.io" "appprojects.argoproj.io"
  kubectl annotate --overwrite crd $crd meta.helm.sh/release-namespace=argo-cd
end
```
