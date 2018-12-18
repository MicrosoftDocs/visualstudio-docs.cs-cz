---
title: '&lt;Podpis&gt; – Element (nasazení ClickOnce) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: fe93a951fdde4a1aa4ad6d2c300551988e42c82b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266945"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Podpis&gt; – Element (nasazení ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obsahuje informace potřebné k digitálnímu podpisu manifestu nasazení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>Poznámky  
 Podpis manifestu nasazení použitím signatury obálky je volitelná, avšak doporučená. Další informace o podepisování XML souborů naleznete v tématu World Wide Web Consortium doporučení, "Syntaxe a zpracování XML – podpis" je popsáno v [ http://www.w3.org/TR/xmldsig-core/ ](http://www.w3.org/TR/xmldsig-core/).  
  
 Pokud chcete pro podepsání manifestu, třeba zadat hodnoty hash pro všechny soubory. Manifest se soubory, které se mají hodnotu hash nelze podepsat, protože uživatelé nemohou ověřit obsah nezašifrované souborů.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `Signature` elementu v manifestu nasazení používané [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení.  
  
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



