---
title: Konfigurace projektu pro výstupní | Microsoft Docs
description: Seznamte se s procesy sestavení, které může každá konfigurace podporovat, a o rozhraních a metodách, pomocí kterých lze výstupní položky získejte.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8b718e70bac0d9e09936daf743420acc04a1c4ad
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899872"
---
# <a name="project-configuration-for-output"></a>Konfigurace projektu pro výstup
Každá konfigurace může podporovat sadu procesů sestavení, které vytvářejí výstupní položky, jako jsou spustitelné soubory nebo soubory prostředků. Tyto výstupní položky jsou pro uživatele soukromé a mohou být umístěny ve skupinách, které propojují související typy výstupu, jako jsou spustitelné soubory (.exe, .dll, .lib) a zdrojové soubory (soubory .idl, .h).

 Výstupní položky mohou být k dispozici prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> metod a výčtu s <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> metodami. Pokud chcete seskupit výstupní položky, měl by projekt také implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> rozhraní.

 Konstruktor vyvinutý implementací `IVsOutputGroup` umožňuje projektům seskupit výstupy podle použití. Knihovna DLL může být například seskupená s programovou databází (PDB).

> [!NOTE]
> Soubor PDB obsahuje informace o ladění a vytvoří se, když je při sestavování souboru .dll nebo .exe. Soubor .pdb se obvykle generuje pouze pro konfiguraci projektu ladění.

 Projekt musí vrátit stejný počet skupin pro každou konfiguraci, kterou podporuje, i když se počet výstupů obsažených ve skupině může lišit od konfigurace po konfiguraci. Například Dll od Uživatele projektu Může obsahovat soubory mattd.dll a <9>d.pdb v konfiguraci ladění, ale zahrnout pouze matt.dll v konfiguraci maloobchodního prodeje.

 Skupiny mají také stejné informace o identifikátorech, jako je kanonický název, zobrazovaný název a informace o skupině, od konfigurace po konfiguraci v rámci projektu. Tato konzistence umožňuje, aby nasazení a balení pokračovalo v provozu i v případě, že se konfigurace změní.

 Skupiny mohou mít také klíčový výstup, který umožňuje, aby zástupci balení odkazovat na něco smysluplného. V dané konfiguraci může být libovolná skupina prázdná, takže byste neměli předpokládat velikost skupiny. Velikost (počet výstupů) každé skupiny v jakékoli konfiguraci se může lišit od velikosti jiné skupiny ve stejné konfiguraci. Může se také lišit od velikosti stejné skupiny v jiné konfiguraci.

 ![Grafické znázornění výstupních skupin](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups") Výstupní skupiny

 Primárním použitím rozhraní je poskytnout přístup k sestavení, nasazení a ladění objektů správy a umožnit projektům volnost <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> seskupování výstupů. Další informace o použití tohoto rozhraní najdete v tématu [Objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md).

 V předchozím diagramu má sestavená skupina klíčový výstup napříč konfiguracemi (bD.exe nebo b.exe), aby uživatel mohl vytvořit zástupce built a vědět, že zástupce bude fungovat bez ohledu na nasazenou konfiguraci. Zdroj skupiny nemá výstup klíče, takže uživatel nemůže vytvořit jeho zástupce. Pokud sestavená skupina ladění má klíčový výstup, ale sestavená maloobchodní skupina ho nemá, byla by to nesprávná implementace. Pak se dozvíte, že pokud nějaká konfigurace obsahuje skupinu, která neobsahuje žádné výstupy, a v důsledku toho žádný soubor klíče, pak ostatní konfigurace této skupiny, které obsahují výstupy, nemohou mít soubory klíčů. Editory instalačního programu předpokládají, že kanonické názvy a zobrazované názvy skupin a existence souboru klíčů se nemění na základě konfigurací.

 Všimněte si, že pokud projekt obsahuje objekt , který nechce zabalit ani nasadit, stačí, když tento výstup `IVsOutputGroup` neumisníte do skupiny. Výstup lze přesto zobrazit normálně implementací metody, která vrací všechny výstupy konfigurace bez ohledu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> na seskupení.

 Další informace najdete v implementaci v ukázce `IVsOutputGroup` vlastního projektu v [MPF for Projects](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="see-also"></a>Viz také
- [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurace projektu pro sestavení](../../extensibility/internals/project-configuration-for-building.md)
- [Objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md)
- [Konfigurace řešení](../../extensibility/internals/solution-configuration.md)
