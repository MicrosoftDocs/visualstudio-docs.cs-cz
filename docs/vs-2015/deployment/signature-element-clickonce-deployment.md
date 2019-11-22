---
title: '&gt; element signatury &lt;(ClickOnce nasazení) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db696546fdd64199753054b38fa2ac554f6a774f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295076"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>Element&gt; Signature &lt;(nasazení ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obsahuje nezbytné informace pro Digitální podepsání tohoto manifestu nasazení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>Poznámky  
 Podpis manifestu nasazení pomocí podpisu obálky je volitelný, ale doporučený. Další informace o podepisování souborů XML naleznete v konsorcium World Wide Web doporučení "XML-Signature and Processing", popsané v [http://www.w3.org/TR/xmldsig-core/](https://www.w3.org/TR/xmldsig-core/).  
  
 Pokud chcete manifest podepsat, je nutné zadat hodnoty hash pro všechny soubory. Manifest se soubory, které nemají hodnotu hash, nelze podepsat, protože uživatelé nemohou ověřit obsah nezatřiďovacích souborů.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `Signature` prvek v manifestu nasazení používaném v nasazení [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
```  
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
  <SignedInfo>  
    <CanonicalizationMethod Algorithm=  
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />  
    <SignatureMethod Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />  
    <Reference URI="">  
      <Transforms>  
        <Transform Algorithm=  
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />  
      </Transforms>  
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <DigestValue>d2z5AE...</DigestValue>  
    </Reference>  
  </SignedInfo>  
  <SignatureValue>  
4PHj6SaopoLp...  
  </SignatureValue>  
  <KeyInfo>  
    <X509Data>  
      <X509Certificate>  
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...  
      </X509Certificate>  
    </X509Data>  
  </KeyInfo>  
</Signature>  
```  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md)
