---
title: Manifesty nasazení pro řešení Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], deployment manifests
- deployment manifests [Office development in Visual Studio]
- manifests [Office development in Visual Studio], deployment
- Office development in Visual Studio, deployment manifests
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 41f0e6b484ae61d53913c51e3d51b123a5d054a2
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34263487"
---
# <a name="deployment-manifests-for-office-solutions"></a>Manifesty nasazení pro řešení Office
  Manifest nasazení je soubor XML, který popisuje nastavení nasazení řešení Office a identifikuje aktuální verze aplikace.  
  
 Vývoj pro Office v sadě Visual Studio použije [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] nasazení manifestu schéma definované v [ClickOnce – manifest nasazení](/visualstudio/deployment/clickonce-deployment-manifest) odkaz.  
  
## <a name="remarks"></a>Poznámky  
 Soubor manifestu nasazení pro řešení Office identifikuje aktuální verze a dalších nastavení nasazení. Odkazuje na manifest aplikace a popisuje aktuální verzi řešení a všechny soubory v rámci v řešení.  
  
## <a name="file-name-syntax"></a>Syntaxe názvu souboru  
 Název souboru manifestu nasazení musí končit *.vsto* rozšíření. I když je standardní [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] – manifest nasazení, se liší povolit Visual Studio Tools for Office runtime pro zpracování souboru rozšíření.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje manifest nasazení pro Visual Studio Tools for Office řešení.  
  
```xml
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly   
  xsi:schemaLocation=  
    "urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"   
  manifestVersion="1.0"   
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"   
  xmlns:dsig="http://www.w3.org/2000/09/xmldsig#"   
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"   
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"   
  xmlns="urn:schemas-microsoft-com:asm.v2"   
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"   
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"   
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"   
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <assemblyIdentity   
    name="ContosoOfficeSolutions.vsto"   
    version="1.0.0.0"   
    publicKeyToken="25d0f3ca94156f1f"   
    language="neutral"   
    processorArchitecture="msil"   
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <description   
    asmv2:publisher="Microsoft"   
    asmv2:product="ContosoOfficeSolutions"   
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <deployment install="false" mapFileExtensions="true" />  
  <dependency>  
    <dependentAssembly   
      dependencyType="install"   
      codebase="ContosoOfficeSolutions.dll.manifest"   
      size="13545">  
      <assemblyIdentity   
        name="ContosoOfficeSolutions.dll"   
        version="1.0.0.0"   
        publicKeyToken="25d0f3ca94156f1f"   
        language="neutral"   
        processorArchitecture="msil"   
        type="win32" />  
      <hash>  
        <dsig:Transforms>  
          <dsig:Transform Algorithm=  
            "urn:schemas-microsoft-com:HashTransforms.Identity" />  
        </dsig:Transforms>  
        <dsig:DigestMethod Algorithm=  
          "http://www.w3.org/2000/09/xmldsig#sha1" />  
        <dsig:DigestValue>PoY</dsig:DigestValue>  
      </hash>  
    </dependentAssembly>  
  </dependency>  
  <publisherIdentity name="name" issuerKeyHash="003" />  
<Signature   
  Id="StrongNameSignature"   
  xmlns="http://www.w3.org/2000/09/xmldsig#">    
  <SignedInfo>  
    <CanonicalizationMethod Algorithm=  
      "http://www.w3.org/2001/10/xml-exc-c14n#" />  
  <SignatureMethod Algorithm=  
    "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
    <Reference URI="">  
      <Transforms>  
        <Transform Algorithm=  
          "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
        <Transform Algorithm=  
          "http://www.w3.org/2001/10/xml-exc-c14n#" />  
      </Transforms>  
      <DigestMethod Algorithm=  
        "http://www.w3.org/2000/09/xmldsig#sha1" />  
      <DigestValue>5oz</DigestValue>  
    </Reference>  
  </SignedInfo>  
  <SignatureValue>nNG</SignatureValue>  
  <KeyInfo Id="StrongNameKeyInfo">  
    <KeyValue>  
      <RSAKeyValue>  
        <Modulus>ufI</Modulus>  
        <Exponent>AQAB</Exponent>  
      </RSAKeyValue>  
    </KeyValue>  
    <msrel:RelData   
      xmlns:msrel=  
        "http://schemas.microsoft.com/windows/rel/2005/reldata">  
      <r:license   
        xmlns:r="urn:mpeg:mpeg21:2003:01-REL-R-NS"   
        xmlns:as=  
          "http://schemas.microsoft.com/windows/pki/2005/Authenticode">  
        <r:grant>  
          <as:ManifestInformation   
            Hash="099"   
            Description=""   
            Url="">  
            <as:assemblyIdentity   
              name="ContosoOfficeSolutions.vsto"   
              version="1.0.0.0"   
              publicKeyToken="25d0f3ca94156f1f"   
              language="neutral"   
              processorArchitecture="msil"   
              xmlns="urn:schemas-microsoft-com:asm.v1" />  
          </as:ManifestInformation>  
          <as:SignedBy />  
          <as:AuthenticodePublisher>  
            <as:X509SubjectName>CN=DDNET\BAAdmin</as:X509SubjectName>  
          </as:AuthenticodePublisher>  
        </r:grant>  
        <r:issuer>  
          <Signature   
            Id="AuthenticodeSignature"   
            xmlns="http://www.w3.org/2000/09/xmldsig#">  
            <SignedInfo>  
              <CanonicalizationMethod   
                Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#" />  
              <SignatureMethod   
                Algorithm=  
                  "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
              <Reference URI="">  
                <Transforms>  
                  <Transform Algorithm=  
                    "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
                  <Transform Algorithm=  
                    "http://www.w3.org/2001/10/xml-exc-c14n#" />  
                </Transforms>  
                <DigestMethod   
                  Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
                <DigestValue>iAd</DigestValue>  
              </Reference>  
            </SignedInfo>  
            <SignatureValue>HL9</SignatureValue>  
            <KeyInfo>  
              <KeyValue>  
                <RSAKeyValue>  
                  <Modulus>ufI</Modulus>  
                  <Exponent>AQAB</Exponent>  
                </RSAKeyValue>  
              </KeyValue>  
              <X509Data>  
                <X509Certificate>MII</X509Certificate>  
              </X509Data>  
            </KeyInfo>  
          </Signature>  
        </r:issuer>  
      </r:license>  
    </msrel:RelData>  
  </KeyInfo>  
</Signature>  
</asmv1:assembly>  
```  
  
## <a name="see-also"></a>Viz také  
 [Manifesty aplikace pro řešení pro systém Office](../vsto/application-manifests-for-office-solutions.md)  
  
  