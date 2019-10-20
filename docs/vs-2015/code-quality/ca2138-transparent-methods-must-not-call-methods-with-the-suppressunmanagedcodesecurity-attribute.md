---
title: 'CA2138: transparentní metody nesmí volat metody s atributem SuppressUnmanagedCodeSecurity | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 65e00d319bff3bbfd3c441c6b60ed8a703e69251
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654805"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: Transparentní metody nesmějí volat metody s atributem SuppressUnmanagedCodeSecurity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Transparentní metoda zabezpečení volá metodu, která je označena atributem <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo je vyvoláno na jakékoli transparentní metodě, která volá přímo do nativního kódu, například pomocí volání metody volání nespravovaného kódu (Invoke). Metody volání nespravovaného volání a modelu COM, které jsou označeny atributem <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>, mají za následek, že se v LinkDemand provádí v rámci volající metody. Vzhledem k tomu, že kód transparentní pro zabezpečení nemůže naplnit LinkDemand, kód také nemůže volat metody, které jsou označeny atributem SuppressUnmanagedCodeSecurity, nebo metody třídy, které jsou označeny atributem SuppressUnmanagedCodeSecurity. Metoda se nezdaří nebo se požadavek převede na úplný požadavek.

 Porušení tohoto pravidla vede na <xref:System.MethodAccessException> v modelu transparentnosti zabezpečení úrovně 2 a na plné poptávce pro <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> v modelu transparentnosti úrovně 1.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, odeberte atribut <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> a označte metodu atributem <xref:System.Security.SecurityCriticalAttribute> nebo <xref:System.Security.SecuritySafeCriticalAttribute>.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2138.transparentmethodsmustnotcallsuppressunmanagedcodesecuritymethods/cs/ca2138.cs#1)]
