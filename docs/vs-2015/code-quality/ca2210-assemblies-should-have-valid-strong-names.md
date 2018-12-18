---
title: 'CA2210: Sestavení by měly mít platné silné názvy | Dokumentace Microsoftu'
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
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1551cccb11fc33a21503e7030cfd671c953ee17d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865814"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: Sestavení by měly mít platné silné názvy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|Kategorie|Microsoft.Design|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina
 Sestavení není podepsáno silným názvem, silného názvu nelze ověřit nebo silný název autoritou nebude platný bez aktuální nastavení registru počítače.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo zjišťuje a ověří silný název sestavení. Porušení nastane, pokud je splněna některá z následujících akcí:

- Sestavení nemá silný název.

- Sestavení byl změněn po podepsání.

- Sestavení se zpožděným podpisem.

- Nesprávně podepsaná sestavení nebo podepisování selhalo.

- Sestavení vyžaduje nastavení registru úspěšně ověřen. Například nástroj Strong Name (Sn.exe) byla použita k přeskočení ověření pro sestavení.

  Silný název chrání klienty před neúmyslným načtením narušeného sestavení. Sestavení bez silných názvů by kromě velmi omezených scénářů neměla být nasazována. Pokud sdílíte nebo šíříte sestavení, která nejsou správně podepsána, může být sestavení záměrně poškozeno, modul CLR je nemusí načíst nebo uživatelé mohou být nuceni vypnout na svém počítači ověřování. Sestavení bez silného názvu se z těchto nevýhod:

- Nelze ověřit jeho původu.

- Modul common language runtime nemůže upozornit uživatele, pokud obsah sestavení byl změněn.

- Nelze načíst do globální mezipaměti sestavení.

  Všimněte si, že se načíst a analyzovat sestavení se zpožděným podpisem, je nutné zakázat ověřování pro sestavení.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 **Chcete-li vytvořit soubor klíče**

 Použijte jednu z následujících postupů:

- Použijte nástroj Assembly Linker (Al.exe) poskytuje [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK.

- Pro [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] v1.0 nebo v1.1, použijte buď <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> nebo <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> atribut.

- Pro [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], použijte buď `/keyfile` nebo `/keycontainer` – možnost kompilátoru [/keyfile (zadat klíč nebo dvojici klíč k podepsání sestavení)](http://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06) nebo  [ /keycontainer (určení kontejneru klíčů pro podpis sestavení)](http://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e) – možnost linkeru v jazyce C++).

  **K podepsání sestavení silným názvem v sadě Visual Studio**

1. V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], otevřete řešení.

2. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a potom klikněte na tlačítko **vlastnosti.**

3. Klikněte na tlačítko **podepisování** kartu a vyberte **podepsat sestavení** zaškrtávací políčko.

4. Z **vyberte soubor klíče se silným názvem**vyberte **nový**.

    **Vytvořit klíč se silným názvem** okně se zobrazí.

5. V **název souboru klíče**, zadejte název pro váš klíč se silným názvem.

6. Zvolte, jestli se k ochraně klíče s heslem a potom klikněte na **OK**.

7. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a potom klikněte na tlačítko **sestavení**.

   **K podepsání sestavení silným názvem mimo sadu Visual Studio**

-   Použijte nástroj pro silný název (Sn.exe), který je poskytován [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK. Další informace najdete v tématu [Sn.exe (nástroj Strong Name)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6).

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pouze potlačit upozornění tohoto pravidla, pokud sestavení se používá v prostředí, kde manipulaci s obsahem není žádný problém.

## <a name="see-also"></a>Viz také
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName><xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
 [Postupy: podepsání sestavení silným názvem](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [Sn.exe (nástroj pro silný název)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)



