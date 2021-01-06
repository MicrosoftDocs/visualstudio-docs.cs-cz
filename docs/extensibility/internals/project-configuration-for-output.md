---
title: Konfigurace projektu pro výstup | Microsoft Docs
description: Přečtěte si o procesech sestavení, které může každá konfigurace podporovat, a o rozhraních a metodách, pomocí kterých lze zpřístupnit výstupní položky.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffe5cb6477808f892b8d36aa5fd616a5a0ea7969
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876321"
---
# <a name="project-configuration-for-output"></a>Konfigurace projektu pro výstup
Každá konfigurace může podporovat sadu procesů sestavení, které vytvářejí výstupní položky, jako jsou spustitelné soubory nebo soubory prostředků. Tyto výstupní položky jsou pro uživatele soukromé a lze je umístit do skupin, které odkazují na související typy výstupu, jako jsou spustitelné soubory (. exe,. dll,. lib) a zdrojové soubory (. idl,. h soubory).

 Výstupní položky mohou být zpřístupněny prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> metod a výčty s <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> metodami. Pokud chcete seskupit výstupní položky, váš projekt by měl také implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> rozhraní.

 Konstrukce vyvinutá implementací `IVsOutputGroup` umožňuje projektům seskupovat výstupy podle využití. Například knihovna DLL může být seskupena s jeho programovou databází (PDB).

> [!NOTE]
> Soubor PDB obsahuje ladicí informace a je vytvořen při zadání možnosti generovat informace o ladění při vytváření souboru. dll nebo. exe. Soubor. pdb je obvykle generován pouze pro ladění konfigurace projektu.

 Projekt musí vracet stejný počet skupin pro každou konfiguraci, kterou podporuje, a to i v případě, že se počet výstupů obsažených v rámci skupiny může lišit od konfigurace až po konfiguraci. Například knihovna DLL podkladu projektu může zahrnovat mattd.dll a matného souboru PDB v konfiguraci ladění, ale zahrne matt.dll pouze v maloobchodní konfiguraci.

 Skupiny mají také stejné informace o identifikátoru, jako je kanonický název, zobrazovaný název a informace o skupině, od konfigurace po konfiguraci v rámci projektu. Tato konzistence umožňuje nasazení a balení i v případě změny konfigurace.

 Skupiny mohou mít také výstup klíče, který umožňuje, aby zástupci balení odkazovali na něco smysluplného. Libovolná skupina může být v dané konfiguraci prázdná, takže nemusíte mít k dispozici žádné předpoklady o velikosti skupiny. Velikost (počet výstupů) každé skupiny v libovolné konfiguraci může být jiná než velikost jiné skupiny ve stejné konfiguraci. Může se také lišit od velikosti stejné skupiny v jiné konfiguraci.

 ![Grafika výstupních skupin](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups") Výstupní skupiny

 Primárním použitím <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> rozhraní je poskytnutí přístupu k sestavování, nasazování a ladění objektů správy a umožňuje projektům volnost ve seskupování výstupů. Další informace o použití tohoto rozhraní naleznete v tématu [objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md).

 V předchozím diagramu má skupina sestavený výstup v různých konfiguracích (bD.exe nebo b.exe), takže uživatel může vytvořit zástupce, který se vytvoří a zjistí, že zástupce bude fungovat bez ohledu na nasazenou konfiguraci. Zdroj skupiny nemá výstup klíče, takže uživatel nemůže pro něj vytvořit zástupce. Pokud má skupina ladění sestavený výstup klíče, ale maloobchodní skupina sestavena nemá, jedná se o nesprávnou implementaci. Následuje, to znamená, že pokud má kterákoli z konfigurací skupinu, která neobsahuje žádné výstupy, a v důsledku toho nebude mít žádný soubor klíče ani jiné konfigurace s touto skupinou, které obsahují výstupy, soubory klíčů. Editory instalačního programu předpokládají, že kanonické názvy a zobrazované názvy skupin a také existenci souboru klíče se nemění v závislosti na konfiguracích.

 Všimněte si, že pokud má projekt `IVsOutputGroup` , který nechce zabalit nebo nasadit, stačí tento výstup vložit do skupiny. Výstup může být v normálním výčtu, protože implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> metodu, která vrátí všechny výstupy konfigurace bez ohledu na seskupení.

 Další informace naleznete v tématu implementace `IVsOutputGroup` v ukázce vlastního projektu v souboru [MPF pro projekty](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="see-also"></a>Viz také
- [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurace projektu pro sestavení](../../extensibility/internals/project-configuration-for-building.md)
- [Objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md)
- [Konfigurace řešení](../../extensibility/internals/solution-configuration.md)
