---
title: Správa sestavení a podepisování manifestu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 98d764bae48fb7deaa3f3cf917b0d4c8baab185b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651372"
---
# <a name="managing-assembly-and-manifest-signing"></a>Správa sestavení a podepsání manifestu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podepisování silného názvu poskytuje komponentě softwaru globálně jedinečnou identitu. Silné názvy slouží k zajištění, že sestavení nemůže být falešné někým jiným a aby se zajistilo, že závislosti komponent a konfigurační příkazy jsou mapovány na správnou komponentu a verzi součásti.

 Silný název se skládá z identity sestavení (jednoduchý textový název, číslo verze a informace o jazykové verzi) a navíc tokenu veřejného klíče a digitálního podpisu.

 Informace o podepisování sestavení v projektech Visual Basic a C# naleznete v tématu [vytváření a používání sestavení se silným názvem](https://msdn.microsoft.com/library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9).

 Informace o podepisování sestavení v Visual C++ projektů naleznete v tématu [sestavení se silným názvem (podepisování sestavení) (C++/CLI)](https://msdn.microsoft.com/library/c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc).

## <a name="asset-types-and-signing"></a>Typy prostředků a podepisování
 Můžete podepsat sestavení .NET a manifesty aplikace. Patří mezi ně následující:

- spustitelné soubory (. exe)

- manifesty aplikace (. exe. manifest)

- manifesty nasazení (. Application)

- sdílená sestavení komponent (. dll)

  Je nutné podepsat následující typy assetu:

1. sestavení, pokud je chcete nasadit do globální mezipaměti sestavení (GAC).

2. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesty aplikací a nasazení. Visual Studio umožňuje přihlášení ve výchozím nastavení pro tyto aplikace.

3. Primární spolupracující sestavení, která se používají pro interoperabilitu modelu COM. Nástroj TLBIMP vynutil silné pojmenovávání při vytváření primárního definičního sestavení z knihovny typů modelu COM.

   Obecně byste neměli podepisovat spustitelné soubory. Komponenta se silným názvem nemůže odkazovat na součást, která není silně pojmenována, která je nasazena s aplikací. Visual Studio nepodepisuje spustitelné soubory aplikace, ale místo toho podepisuje manifest aplikace, který odkazuje na spustitelný soubor se slabým názvem. Obecně byste se měli vyhnout podepisování komponent, které jsou pro vaši aplikaci soukromé, protože podepisování může ztížit správu závislostí.

## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Jak podepsat sestavení v aplikaci Visual Studio
 Aplikaci nebo komponentu podepisujete pomocí karty **podepisování** v okně Vlastnosti projektu (klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a vyberte **vlastnosti**, nebo zadejte **Vlastnosti projektu** v okně **Snadné spuštění** nebo stiskněte klávesovou zkratku ALT + ENTER uvnitř okna **Průzkumník řešení** ). Vyberte kartu **podepisování** a potom zaškrtněte políčko **podepsat sestavení**  .

 Zadejte soubor klíče. Pokud se rozhodnete vytvořit nový soubor klíče, Všimněte si, že nové soubory klíčů jsou vždy vytvořeny ve formátu. pfx. Pro nový soubor budete potřebovat jméno a heslo.

> [!WARNING]
> Soubor klíče byste měli vždycky chránit heslem, abyste zabránili jeho použití někomu jinému. Klíče můžete zabezpečit i pomocí poskytovatelů nebo úložišť certifikátů.

 Můžete také Ukázat na klíč, který jste už vytvořili. Další informace o vytváření klíčů naleznete v tématu [How to: Create a Public-Private Key páru](https://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114).

 Máte-li přístup pouze k veřejnému klíči, můžete použít zpožděné podepisování k odložení přiřazení klíče. Zpožděné podepisování povolíte zaškrtnutím políčka **pouze zpožděné přihlášení** . Projekt se zpožděným podpisem se nespustí a nemůžete ho ladit. Ověřování však můžete během vývoje přeskočit pomocí možnosti [Sn.exe (Nástroj pro silný název)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6) `-Vr` .

 Informace o podepisování manifestů naleznete v tématu [How to: Signing Application and Deployment Manifests](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="see-also"></a>Viz také
 Sestavení silného názvu [sestavení](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b) se silným názvem [(podepisování sestavení) (C++/CLI)](https://msdn.microsoft.com/library/c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc)
