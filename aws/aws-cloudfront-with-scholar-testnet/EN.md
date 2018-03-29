# Amazon Web Services

## AWS Cloudfront with ScholarTestnet

Setting up a website using GitHub pages is one of the easiest ways to publish a custom website without having to pay for any web hosting costs. You simply need to add `index.html` to your root repository and click publish in the settings. One of the downsides of using GitHub Pages is the inability of hosting a custom domain over SSL (encrypted & secure website).

Here’s what we will cover during this tutorial:

- Setting up a website using GitHub Pages
- Requesting a SSL Certificate from AWS
- Configuration AWS Cloudfront
- Route your CNAME using AWS Route 53

### Setting up a website using GitHub Pages

Include an `index.html` in the root directory of one of your GitHub repositories, then go to **(settings)** and enable GitHub Pages. You can include a custom domain name, however SSL is not supported for custom domains.

For an example, we’ve already configured the ScholarTesnet using GitHub Pages:

https://github.com/ScholarTestnet/ScholarTestnet.github.io

![image](https://user-images.githubusercontent.com/550895/38103012-17a6c49e-3353-11e8-95e3-67f7757e6308.png)

### Requesting a SSL Certificate from AWS

Go to **Services** => **Certificate Manager** => **Request Certificate**

In the top-right corner, make sure you are on **US East (N. Virginia)**, as the certificate must be provisioned in that region in order to be detected by CloudFront in the future steps.

<img src="https://user-images.githubusercontent.com/550895/38103041-32bd1f4e-3353-11e8-8397-ac8e24a4644a.png" width=300/>

Add your root domain and a wildcard for any subdomain that you wish to add in the future (most common one would be `www`).

<img src="https://user-images.githubusercontent.com/550895/38103053-3e47c800-3353-11e8-821f-4f56836d5fc4.png" width=300/>

Complete the DNS Validation or Email Validation, if you chose DNS Validation you can have AWS create the 53 Route records via a simple click.

### Configuration AWS Cloudfront

Go to **Services** => **CloudFront Distributions** => **Create Distribution** => **Web / Get Started**

Add your GitHub pages URL to **Origin Domain Name**.

> Note: if you have many GitHub pages under the same GitHub organization, you will need to specify the specific project by including it in the **Origin Path**.

<img src="https://user-images.githubusercontent.com/550895/38103082-5c100aaa-3353-11e8-88f7-dd40a5767e0f.png" width=300/>

Change the **Viewer Protocol Policy** to **“Redirect HTTP to HTTPS”** that way all your viewers will be redirected to only a secure HTTPS website.

<img src="https://user-images.githubusercontent.com/550895/38103102-6d8154ce-3353-11e8-985f-74acc7d9ec23.png" width=400/>

Include your subdomain to **“Alternate Domain Names (CNAMEs)”**. The domain name must match your SSL Certificate you created earlier.

Second, include Custom SSL Certificate by choosing the name of your SSL certificate.

![image](https://user-images.githubusercontent.com/550895/38103121-7fd65b74-3353-11e8-84f4-c41d2f39ca7a.png)

All other settings can be kept as the default.

Select **“Create Distribution”**

You should now see a new Distribution with a cloudfront.net URL under **Domain Name**, this URL will be included as a CNAME using Route 53.

![image](https://user-images.githubusercontent.com/550895/38103139-8f92329a-3353-11e8-9f84-d6b0c5202901.png)

### Route your CNAME using AWS Route 53

Go to **Services** => **Route 53** => **Hosted Zones**

Select one of the hosted zones which you used as the domain name for your GitHub Pages.

Select **Create Record Set** create a CNAME record using the cloudfront URL.

<img src="https://user-images.githubusercontent.com/550895/38103171-a85f3750-3353-11e8-96f7-fcfbfac55036.png" width=400/>

### Completed

After these configurations are finally set up, you should be able to see your GitHub pages website hosted with your custom domain name running over SSL (secure/encrypted website).

https://scholar.eosnation.io

![image](https://user-images.githubusercontent.com/550895/38103201-bbc44132-3353-11e8-9d1b-644665b8ca82.png)
