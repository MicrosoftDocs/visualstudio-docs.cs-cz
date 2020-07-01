---
title: 'CA2100: Projděte si dotazy SQL na chyby zabezpečení | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 797c071cdc74c36afeece304bfa4c708d7bf7147
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521209"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: Zkontrolujte chyby zabezpečení u dotazů SQL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|Kategorie|Microsoft.Security|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Metoda nastavuje <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> vlastnost pomocí řetězce, který je sestaven z řetězcového argumentu metody.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo předpokládá, že řetězcový argument obsahuje vstup uživatele. Řetězec příkazu SQL sestavený ze vstupu uživatele je ohrožen útoky prostřednictvím injektáže SQL. V případě útoku prostřednictvím injektáže SQL uživatel se zlými úmysly dodává vstup, který mění návrh dotazu při pokusu o poškození nebo získání neoprávněného přístupu k podkladové databázi. Mezi obvyklé techniky patří vložení jednoduché uvozovky nebo apostrofu, což je oddělovač řetězcového literálu SQL. dvě pomlčky, což znamená komentář SQL; a středníkem, který indikuje, že následuje nový příkaz. Pokud musí být vstup uživatele součástí dotazu, použijte jednu z následujících možností, která je uvedena v řádu účinnosti, aby se snížilo riziko útoku.

- Použijte uloženou proceduru.

- Použijte parametrizovaný řetězec příkazu.

- Před sestavením řetězce příkazu ověřte vstup uživatele pro typ i obsah.

  Následující [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] typy implementují <xref:System.Data.IDbCommand.CommandText%2A> vlastnost nebo poskytují konstruktory, které nastavují vlastnost pomocí řetězcového argumentu.

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> a <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> a <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> a <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

- [System. data. SqlServerCe. SqlCeCommand] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&amp;autoUpgrade=True>  -->) a [System. data. SqlServerCe. SqlCeDataAdapter] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&amp;autoUpgrade=True>  -->)

- <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> a <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

  Všimněte si, že toto pravidlo je porušené, když se metoda ToString typu používá explicitně nebo implicitně k sestavení řetězce dotazu. Následuje příklad.

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 Toto pravidlo je porušeno, protože uživatel se zlými úmysly může přepsat metodu ToString ().

 Toto pravidlo je porušeno také v případě implicitního použití ToString.

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, použijte parametrizovaný dotaz.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud text příkazu neobsahuje žádný vstup uživatele, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu,, `UnsafeQuery` která porušuje pravidlo a metodu, `SaferQuery` ,, který splňuje pravidlo pomocí parametrizovaného řetězce příkazu.

 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cpp/FxCop.Security.ReviewSqlQueries.cpp#1)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cs/FxCop.Security.ReviewSqlQueries.cs#1)]
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/vb/FxCop.Security.ReviewSqlQueries.vb#1)]

## <a name="see-also"></a>Viz také
 [Přehled zabezpečení](https://msdn.microsoft.com/library/33e09965-61d5-48cc-9e8c-3b047cc4f194)
