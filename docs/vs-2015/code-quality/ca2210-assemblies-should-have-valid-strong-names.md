---
title: 'CA2210: sestavení by měly mít platné silné názvy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6109e0dc18f98d0b22dfb5c548bd12447b53e61d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662984"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: Sestavení by měly mít platné silné názvy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|Kategorie|Microsoft. Design|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>příčina
 Sestavení není podepsáno silným názvem, nelze ověřit silný název nebo silný název nebude platný bez aktuálního nastavení registru počítače.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo načte a ověří silný název sestavení. K porušení dojde, pokud platí některá z následujících podmínek:

- Sestavení nemá silný název.

- Sestavení bylo po podepsání změněno.

- Sestavení je podepsané se zpožděním.

- Sestavení bylo nesprávně podepsáno nebo se nezdařilo podepisování.

- Sestavení vyžaduje k předání ověření nastavení registru. Například nástroj silného názvu (Sn. exe) se použil k přeskočení ověření pro sestavení.

  Silný název chrání klienty před neúmyslným načtením narušeného sestavení. Sestavení bez silných názvů by kromě velmi omezených scénářů neměla být nasazována. Pokud sdílíte nebo šíříte sestavení, která nejsou správně podepsána, může být sestavení záměrně poškozeno, modul CLR je nemusí načíst nebo uživatelé mohou být nuceni vypnout na svém počítači ověřování. Sestavení bez silného názvu má z následujících nevýhod:

- Původce nelze ověřit.

- Modul CLR (Common Language Runtime) nemůže varovat uživatele, pokud došlo ke změně obsahu sestavení.

- Nelze jej načíst do globální mezipaměti sestavení (GAC).

  Všimněte si, že pro načtení a analýzu sestavení se zpožděným podpisem je nutné zakázat ověření pro sestavení.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 **Vytvoření souboru klíče**

 Použijte jeden z následujících postupů:

- Použijte nástroj Assembly Linker (Al. exe), který poskytuje sada [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK.

- Pro [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] v 1.0 nebo v 1.1 použijte buď atribut <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> nebo <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>.

- Pro [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] použijte buď možnost kompilátoru `/keyfile` nebo `/keycontainer` [/keyfile (zadejte klíč nebo dvojici klíčů pro podepsání sestavení)](https://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06) nebo [/keycontainer (zadejte kontejner klíčů pro podepsání sestavení)](https://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e) možnost linkeru v aplikaci C++).

  **Podepsání sestavení silným názvem v aplikaci Visual Studio**

1. V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] otevřete své řešení.

2. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a pak klikněte na **Vlastnosti.**

3. Klikněte na kartu **podepisování** a zaškrtněte políčko **podepsat sestavení** .

4. V **Možnosti zvolit soubor klíče se silným názvem**vyberte **Nový**.

    Zobrazí se okno **vytvořit klíč se silným názvem** .

5. Do klíčového **názvu souboru**zadejte název klíče se silným názvem.

6. Zvolte, zda chcete klíč chránit heslem, a poté klikněte na tlačítko **OK**.

7. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a potom klikněte na položku **sestavit**.

   **Podepsání sestavení silným názvem mimo Visual Studio**

- Použijte nástroj se silným názvem (Sn. exe), který je k dispozici v sadě [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK. Další informace naleznete v tématu [sn. exe (Nástroj pro silný název)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6).

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačí upozornění z tohoto pravidla pouze v případě, že je sestavení použito v prostředí, ve kterém není manipulace s obsahem netýká se.

## <a name="see-also"></a>Viz také
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName><xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
 [Postupy: podepsání sestavení silným názvem](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [sn. exe (Nástroj pro silný název)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)
