---
title: Správa podepsání sestavení a manifestu
ms.date: 02/17/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb2113ed091d99ed66b13955ea468c376bba9490
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2018
ms.locfileid: "39379563"
---
# <a name="manage-assembly-and-manifest-signing"></a>Správa podepsání sestavení a manifestu

Podepisování silným názvem poskytuje softwarová součást globálně jedinečné identity. Silné názvy se používají k zajištění, že s falešnou identitou sestavení někým jiným a ujistěte se, že závislostí součástí a konfigurace příkazy, které se mapují správné komponenty a verze komponenty.

Silný název se skládá z identity sestavení (jednoduchý textový název, číslo verze a informace o jazykové verzi), plus token veřejného klíče a digitální podpis.

Informace o podepisování sestavení v projektech Visual Basic a C# najdete v tématu [vytvoření a použití sestavení se silným názvem](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies).

Informace o podepisování sestavení v projektech Visual C++, naleznete v tématu [sestavení se silným názvem (C + +/ CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli).

> [!NOTE]
> Podepisování silným názvem neposkytuje ochranu proti zpětné analýzy sestavení. K ochraně proti zpětné analýzy, najdete v článku [nástroj Dotfuscator Community Edition (CE)](dotfuscator/index.md).

## <a name="asset-types-and-signing"></a>Typy prostředků a podepisování

Je možné podepsat manifesty aplikace a sestavení .NET:

- Spustitelné soubory (*.exe*)

- Manifesty aplikací (*. exe.manifest*)

- Manifesty nasazení (*.application*)

- Sdílená sestavení součásti (*.dll*)

Podepište následující typy prostředků:

1. Sestavení, pokud chcete nasadit do globální mezipaměti sestavení (GAC).

2. Manifesty aplikace a nasazení ClickOnce. Visual Studio umožňuje podepisování ve výchozím nastavení v případě těchto aplikací.

3. Primární spolupracující sestavení, které se používají pro interoperabilitu COM. Nástroj TLBIMP vynucuje silné názvy při vytváření primárních sestavení vzájemné spolupráce z knihovny typů modelu COM.

Obecně platí neměli podepisovat spustitelné soubory. Silný název komponenty nemůže odkazovat na komponenty bez silným názvem, který je nasazen s aplikací. Uživatel spustitelné soubory aplikace Visual Studio, ale místo toho podepíše manifest aplikace, která odkazuje na spustitelný soubor s názvem slabé. Vyhněte se podepisování součásti, které jsou privátní pro vaši aplikaci, protože podepisování může to ztížit Spravovat závislosti.

## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Podepsání sestavení v sadě Visual Studio

Podepsání aplikace nebo komponenty pomocí **podepisování** karty v okně Vlastnosti projektu (klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a vyberte **vlastnosti**, nebo typ **vlastnosti projektu** v **Snadné spuštění** okna, nebo stisknutím klávesy **Alt**+**Enter** uvnitř **Průzkumníka řešení**). Vyberte **podepisování** kartu a potom vyberte **podepsat sestavení** zaškrtávací políčko.

Zadejte soubor klíče. Pokud budete chtít vytvořit nový soubor klíče, jsou vždy vytváří nové soubory klíčů v *.pfx* formátu. Budete potřebovat jméno a heslo pro nový soubor.

> [!WARNING]
> Vždy byste měli chránit vašemu souboru s klíčem s heslem někdo zabránit jeho použití. Klíče můžete zabezpečit také pomocí zprostředkovatele nebo úložiště certifikátů.

Může také odkazovat na klíč, který jste už vytvořili. Další informace o vytváření klíčů najdete v tématu [vytvoření páru veřejného a privátního klíče](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).

Pokud máte jenom přístup k veřejným klíčem, můžete použít dodatečném podepisování odložení přiřazení klíč. Povolit zpoždění podepsání tak, že vyberete **zpoždění podepsání** zaškrtávací políčko. Projekt se zpožděným podpisem se nespustí a nelze ho ladit. Však můžete přeskočit ověření během vývoje s použitím [nástroj pro silný název Sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) s `-Vr` možnost.

Informace o podepisování manifestů naleznete v tématu [postupy: podepsání manifestů aplikace a nasazení](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="see-also"></a>Viz také:

- [Sestavení se silným názvem](/dotnet/framework/app-domains/strong-named-assemblies)
- [Sestavení se silným názvem (C + +/ CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)
