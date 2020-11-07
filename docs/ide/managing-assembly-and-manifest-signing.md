---
title: Správa podepsání sestavení a manifestu
description: Seznamte se s výhodami podepisování silného názvu, který poskytuje komponentě softwaru globálně jedinečnou identitu.
ms.custom: SEO-VS-2020
ms.date: 02/17/2017
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bdd2570f94b0f5577c7c09a696906338245f77a4
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351385"
---
# <a name="manage-assembly-and-manifest-signing"></a>Správa podepsání sestavení a manifestu

Podepisování silného názvu poskytuje komponentě softwaru globálně jedinečnou identitu. Silné názvy slouží k zajištění toho, že sestavení nemůže být falešné někým jiným a aby se zajistilo, že závislosti komponent a konfigurační příkazy jsou mapovány na správnou komponentu a verzi komponenty.

Silný název se skládá z identity sestavení (jednoduchý textový název, číslo verze a informace o jazykové verzi) a navíc tokenu veřejného klíče a digitálního podpisu.

Informace o podepisování sestavení v projektech Visual Basic a C# najdete v tématu [Vytvoření a použití sestavení se silným názvem](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies).

Informace o podepisování sestavení v projektech C++ naleznete v tématu [sestavení se silným názvem (C++/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli).

> [!NOTE]
> Podepisování silného názvu není chráněno proti zpětné analýze sestavení. Informace o ochraně před zpětným inženýrstvím najdete v tématu [komunita Dotfuscator](dotfuscator/index.md).

## <a name="asset-types-and-signing"></a>Typy prostředků a podepisování

Můžete podepsat sestavení .NET a manifesty aplikace:

- Spustitelné soubory ( *. exe* )

- Manifesty aplikace ( *. exe. manifest* )

- Manifesty nasazení ( *. Application* )

- Sdílená sestavení komponent ( *. dll* )

Podepište následující typy assetu:

1. Sestavení, pokud je chcete nasadit do globální mezipaměti sestavení (GAC).

2. ClickOnce aplikace a manifesty nasazení. Visual Studio umožňuje přihlášení ve výchozím nastavení pro tyto aplikace.

3. Primární spolupracující sestavení, která se používají pro interoperabilitu modelu COM. Nástroj TLBIMP vynutil silné pojmenovávání při vytváření primárního definičního sestavení z knihovny typů modelu COM.

Obecně platí, že byste neměli podepisovat spustitelné soubory. Silně pojmenovaná komponenta nemůže odkazovat na součást, která není silně pojmenována, která je nasazena s aplikací. Visual Studio nepodepisuje spustitelné soubory aplikace, ale místo toho podepisuje manifest aplikace, který odkazuje na spustitelný soubor se slabým názvem. Vyhněte se podepisování součástí, které jsou pro vaši aplikaci soukromé, protože podepisování může ztížit správu závislostí.

## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Jak podepsat sestavení v aplikaci Visual Studio

Aplikaci nebo komponentu podepisujete pomocí karty **podepisování** v okně Vlastnosti projektu (klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a vyberte **vlastnosti** ). Vyberte kartu **podepisování** a potom zaškrtněte políčko **podepsat sestavení**  .

Zadejte soubor klíče. Pokud se rozhodnete vytvořit nový soubor klíče, budou nové soubory klíčů vždy vytvořeny ve formátu *. pfx* . Pro nový soubor budete potřebovat jméno a heslo.

> [!WARNING]
> Soubor klíče byste měli vždycky chránit heslem, abyste zabránili jeho použití někomu jinému. Klíče můžete zabezpečit i pomocí poskytovatelů nebo úložišť certifikátů.

Můžete také Ukázat na klíč, který jste už vytvořili. Další informace o vytváření klíčů najdete v tématu [vytvoření dvojice klíčů veřejného a soukromého klíče](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).

Pokud máte přístup jenom k veřejnému klíči, můžete k odložení přiřazení klíče použít zpožděné podepisování. Zpožděné podepisování povolíte zaškrtnutím políčka **pouze zpožděné přihlášení** . Projekt se zpožděným podpisem se nespustí a nemůžete ho ladit. Ověřování však můžete během vývoje přeskočit pomocí [ nástrojeSn.exe silný název](/dotnet/framework/tools/sn-exe-strong-name-tool) s `-Vr` možností.

Informace o podepisování manifestů naleznete v tématu [How to: Signing Application and Deployment Manifests](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="see-also"></a>Viz také

- [Sestavení se silným názvem](/dotnet/framework/app-domains/strong-named-assemblies)
- [Sestavení se silným názvem (C++/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)
