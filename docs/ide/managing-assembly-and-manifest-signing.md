---
title: Správa podepsání sestavení a manifestu
ms.date: 02/17/2017
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f13df00059523ca87e720a999c596e203b20e49
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593678"
---
# <a name="manage-assembly-and-manifest-signing"></a>Správa podepsání sestavení a manifestu

Podepisování silného názvu poskytuje softwarové součásti globálně jedinečnou identitu. Silné názvy se používají k zajištění toho, že sestavení nemůže být zfalšováno jiným uživatelem, a ujistěte se, že závislosti komponent a příkazy konfigurace jsou mapovány na správnou verzi komponenty a součásti.

Silný název se skládá z identity sestavení (jednoduchý textový název, číslo verze a informace o jazykové verzi) plus token veřejného klíče a digitální podpis.

Informace o podepisování sestavení v projektech jazyka Visual Basic a C# naleznete v [tématu Vytvoření a použití sestavení se silným názvem](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies).

Informace o podpisu sestavení v projektech jazyka C++ naleznete v [tématu sestavení s názvem Silné (C++/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli).

> [!NOTE]
> Podepisování silného názvu nechrání před zpětnou analýzou sestavení. Chcete-li se chránit před zpětným inženýrstvím, viz [Dotfuscator Community](dotfuscator/index.md).

## <a name="asset-types-and-signing"></a>Typy majetku a podepisování

Můžete podepsat sestavení .NET a manifesty aplikací:

- Spustitelné soubory (*.exe*)

- Manifesty aplikace (*.exe.manifest*)

- Manifesty nasazení (*.application*)

- Sestavy sdílených součástí (*DLL*)

Podepište následující typy majetku:

1. Sestavení, pokud je chcete nasadit do globální mezipaměti sestavení (GAC).

2. Manifesty aplikace a nasazení clickonce. Visual Studio umožňuje podepisování ve výchozím nastavení pro tyto aplikace.

3. Primární sestavení interop, které se používají pro interoperabilitu com. Nástroj TLBIMP vynucuje silné pojmenování při vytváření primárního sestavení interop z knihovny typů COM.

Obecně byste neměli podepisovat spustitelné soubory. Silně pojmenovaná komponenta nemůže odkazovat na komponentu bez silného označení, která je nasazena s aplikací. Visual Studio nepodepisuje spustitelné soubory aplikace, ale místo toho podepisuje manifest aplikace, který odkazuje na spustitelný soubor se slabým názvem. Vyhněte se podepisování součástí, které jsou soukromé pro vaši aplikaci, protože podepisování může ztížit správu závislostí.

## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Jak podepsat sestavení v sadě Visual Studio

Aplikaci nebo komponentu podepíšete pomocí karty **Podpis** v okně vlastností projektu (klepněte pravým tlačítkem myši na uzel projektu v **Průzkumníku řešení** a vyberte **vlastnosti**). Vyberte kartu **Podpisy** a zaškrtněte políčko **Podepsat sestavení.**

Zadejte soubor klíče. Pokud se rozhodnete vytvořit nový soubor klíče, budou nové soubory klíčů vždy vytvořeny ve formátu *.pfx.* Potřebujete jméno a heslo pro nový soubor.

> [!WARNING]
> Soubor klíče byste měli vždy chránit heslem, abyste zabránili jeho použití někomu jinému. Klíče můžete také zabezpečit pomocí zprostředkovatelů nebo úložišť certifikátů.

Můžete také překážet na klíč, který jste již vytvořili. Další informace o vytváření klíčů naleznete [v tématu Vytvoření páru veřejných a soukromých klíčů](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).

Pokud máte přístup pouze k veřejnému klíči, můžete k odložení přiřazení klíče použít podepisování zpoždění. Podpis zpoždění povolíte zaškrtnutím políčka **Pouze znaménko Zpoždění.** Projekt podepsaný zpožděním nespustí a nelze jej ladit. Ověření během vývoje však můžete přeskočit pomocí [nástroje silného názvu Sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) s možností. `-Vr`

Informace o podepisování manifestů naleznete v [tématu How to: Sign application and deployment manifests](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="see-also"></a>Viz také

- [Sestavení se silným názvem](/dotnet/framework/app-domains/strong-named-assemblies)
- [Sestavení se silným názvem (C++/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)
