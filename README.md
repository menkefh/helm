## TLDR;
```
helm % helm install --namespace "graylog" -n "graylog" kong-z/graylog --set graylog.externalUri=<<externalname>> --set graylog.image.repository=graylog/graylog:<<latest version i.e 4.0.9>> --generate-name
```

## Post install
1. you can find the generated name in the
 "Output generated from the helm install command"

2. run the echo "User...." etc. from the output to get teh graylog admin password.


3. modify ingress service to point to:
 graylog-xxxxxxxxxx
  generated name

## To upgrade
```
helm upgrade graylog-1628189340 --set name=1628189340 --namespace "graylog" -n "graylog" kong-z/graylog --set graylog.image.repository=graylog/graylog:<<version>>  --set graylog.externalUri=<<external ip/name>> --set graylog.replicas=3
```
You may need to scale your stateful sets to more than one
mongodb
mongodb-arbiter
elasticsearch-data
elasticsearch-master
## Notes on using on a local cluster

1. You may need to do a docker login and docker pull graylog/graylog:<<version you want>> to get the image first

[remove the webhook if you get an error adding the ingress rules](https://stackoverflow.com/questions/61365202/nginx-ingress-service-ingress-nginx-controller-admission-not-found)
```
kubectl delete -A ValidatingWebhookConfiguration ingress-nginx-admission
```
You can use the [editor on GitHub](https://github.com/menkefh/helm/edit/gh-pages/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/menkefh/helm/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
