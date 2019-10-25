---
title: '&gt; element signatury &lt;(ClickOnce nasazení) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f69dcec6bbee5358184b74a71274cb26e4de60b3
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806843"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>element&gt; Signature &lt;(nasazení ClickOnce)
Obsahuje nezbytné informace pro Digitální podepsání tohoto manifestu nasazení.

## <a name="syntax"></a>Syntaxe

```xml

      <Signature> 
   XML signature information 
</Signature>
```

## <a name="remarks"></a>Poznámky
 Podpis manifestu nasazení pomocí podpisu obálky je volitelný, ale doporučený. Další informace o podepisování souborů XML naleznete v konsorcium World Wide Web doporučení "XML – signatura a zpracování", popsané v [http://www.w3.org/TR/xmldsig-core/](https://www.w3.org/TR/xmldsig-core/).

 Pokud chcete manifest podepsat, je nutné zadat hodnoty hash pro všechny soubory. Manifest se soubory, které nemají hodnotu hash, nelze podepsat, protože uživatelé nemohou ověřit obsah nezatřiďovacích souborů.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje `Signature` prvek v manifestu nasazení používaném v nasazení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

```xml
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

## <a name="see-also"></a>Viz také:
- [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md)