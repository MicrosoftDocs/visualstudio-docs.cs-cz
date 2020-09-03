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
ms.openlocfilehash: 35cc152998b15a2fd4c4ff02e4730cdfae5366cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546494"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: Transparentní metody nesmí volat metody s atributem SuppressUnmanagedCodeSecurity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Transparentní metoda zabezpečení volá metodu, která je označena <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributem.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo je vyvoláno na jakékoli transparentní metodě, která volá přímo do nativního kódu, například pomocí volání metody volání nespravovaného kódu (Invoke). Metody volání nespravovaného volání a modelu COM, které jsou označeny <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributem Result, mají za následek, že se v LinkDemand provádí v rámci volající metody. Vzhledem k tomu, že kód transparentní pro zabezpečení nemůže naplnit LinkDemand, kód také nemůže volat metody, které jsou označeny atributem SuppressUnmanagedCodeSecurity, nebo metody třídy, které jsou označeny atributem SuppressUnmanagedCodeSecurity. Metoda se nezdaří nebo se požadavek převede na úplný požadavek.

 Porušení tohoto pravidla povedou k tomu <xref:System.MethodAccessException> , že v modelu transparentnosti úrovně 2 a v modelu transparentnosti úrovně 1 máte plnou poptávku <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> .

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, odeberte <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atribut a označte metodu <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> atributem nebo.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2138.transparentmethodsmustnotcallsuppressunmanagedcodesecuritymethods/cs/ca2138.cs#1)]
