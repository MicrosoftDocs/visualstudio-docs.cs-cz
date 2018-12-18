---
title: 'CA2100: Revize dotazů SQL pro chyby zabezpečení | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c77e448a492a64e3bbdf0f86809cdf82d7fd72fa
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877397"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: Revize dotazů SQL pro chyby zabezpečení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|Kategorie|Microsoft.Security|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Nastaví metodu <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> vlastnost s použitím řetězec, který je sestaven z řetězcového argumentu k metodě.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo předpokládá, že řetězcový argument obsahuje vstup uživatele. Řetězec příkazu SQL sestavený ze vstupu uživatele je ohrožen útoky prostřednictvím injektáže SQL. Při útoku prostřednictvím injektáže SQL uživatel se zlými úmysly zadává vstup, který mění návrh dotazu ve snaze poškodit nebo získání neoprávněného přístupu k podkladové databázi. Mezi typické dostupné techniky patří vkládání jednoduchá uvozovka nebo apostrof, což je oddělovač řetězcového literálu SQL; dva spojovníky, které označuje, že komentář SQL; a středník, což znamená, že nový příkaz následuje. Pokud uživatelský vstup musí být část dotazu, použijte některou z těchto možností uvedeny v pořadí podle účinnosti, aby se snížilo riziko útoku.

- Použití uložené procedury.

- Použití parametrizovaného příkazu řetězce.

- Ověření vstupu uživatele pro typ a obsah, před sestavením řetězec příkazu.

  Následující [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] typy implementovat <xref:System.Data.IDbCommand.CommandText%2A> vlastnost nebo zadejte konstruktory, které se nastavit vlastnost použitím argumentu řetězce.

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> a <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> a <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> a <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

- [System.Data.SqlServerCe.SqlCeCommand] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&amp;autoUpgrade=True>  -->) a [System.Data.SqlServerCe.SqlCeDataAdapter] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&amp;autoUpgrade=True>  -->)

- <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> a <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

  Všimněte si, že při použití metody ToString typu explicitně nebo implicitně porušení tohoto pravidla k vytvoření řetězce dotazu. Následuje příklad.

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 Porušení pravidla vzhledem k tomu, že uživatel se zlými úmysly může přepsat metodu ToString().

 Toto pravidlo je také poruší, když se implicitně používá ToString.

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, použijte parametrický dotaz.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla, je-li text příkazu neobsahuje vstupu uživatele.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, `UnsafeQuery`, který porušuje pravidla a metodu, `SaferQuery`, který splňuje pravidlo s použitím řetězec parametrizovaného příkazu.

 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cpp/FxCop.Security.ReviewSqlQueries.cpp#1)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cs/FxCop.Security.ReviewSqlQueries.cs#1)]
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/vb/FxCop.Security.ReviewSqlQueries.vb#1)]

## <a name="see-also"></a>Viz také
 [Přehled zabezpečení](http://msdn.microsoft.com/library/33e09965-61d5-48cc-9e8c-3b047cc4f194)



