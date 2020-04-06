---
title: Konfigurace projektu pro výstup | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 78b95457af4c5d806fdfcc20f49ac4e82df36488
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706671"
---
# <a name="project-configuration-for-output"></a>Konfigurace projektu pro výstup
Každá konfigurace může podporovat sadu procesů sestavení, které vytvářejí výstupní položky, jako jsou spustitelné soubory nebo soubory prostředků. Tyto výstupní položky jsou pro uživatele soukromé a mohou být umístěny ve skupinách, které propojují související typy výstupu, jako jsou spustitelné soubory (.exe, dll, .lib) a zdrojové soubory (.idl, .h files).

 Výstupní položky mohou být <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> k dispozici prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> metod a výčtu s metodami. Pokud chcete seskupit výstupní položky, projekt by měl také implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> rozhraní.

 Konstrukce vyvinutá implementací `IVsOutputGroup` umožňuje projektům seskupit výstupy podle využití. Například dll může být seskupeny s jeho programdatabáze (PDB).

> [!NOTE]
> Soubor PDB obsahuje informace o ladění a je vytvořen při vytváření možnosti Generovat informace o ladění při vytváření souboru DLL nebo .exe. Soubor PDB je obvykle generován pouze pro konfiguraci projektu ladění.

 Projekt musí vrátit stejný počet skupin pro každou konfiguraci, kterou podporuje, i když počet výstupů obsažených ve skupině se může lišit od konfigurace ke konfiguraci. Například dll projektu Matt může obsahovat mattd.dll a mattd.pdb v konfiguraci ladění, ale zahrnout pouze matt.dll v konfiguraci Maloobchod.

 Skupiny mají také stejné informace o identifikátoru, například kanonický název, zobrazovaný název a informace o skupině, od konfigurace až po konfiguraci v rámci projektu. Tato konzistence umožňuje nasazení a balení nadále fungovat i v případě, že konfigurace změnit.

 Skupiny mohou mít také klíčový výstup, který umožňuje zástupci balení přejděte na něco smysluplného. Každá skupina může být v dané konfiguraci prázdná, takže by neměly být provedeny žádné předpoklady o velikosti skupiny. Velikost (počet výstupů) každé skupiny v libovolné konfiguraci se může lišit od velikosti jiné skupiny ve stejné konfiguraci. Může se také lišit od velikosti stejné skupiny v jiné konfiguraci.

 ![Obrázek Skupiny výstupů](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups") Výstupní skupiny

 Primární použití <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> rozhraní je poskytnout přístup k sestavení, nasazení a ladění objektů správy a umožnit projektům svobodu seskupit výstupy. Další informace o použití tohoto rozhraní naleznete v tématu [Project Configuration Object](../../extensibility/internals/project-configuration-object.md).

 V předchozím diagramu má skupina Vytvořeno klíčový výstup napříč konfiguracemi (buď bD.exe nebo b.exe), takže uživatel může vytvořit zástupce Built a vědět, že zástupce bude fungovat bez ohledu na nasazenou konfiguraci. Zdroj skupiny nemá klíčový výstup, takže uživatel nemůže vytvořit zástupce. Pokud ladicí skupina Built má výstup klíče, ale maloobchodní skupina built není, to by bylo nesprávné implementace. Z toho vyplývá, že pokud má libovolná konfigurace skupinu, která neobsahuje žádné výstupy, a v důsledku toho žádný soubor klíče, pak jiné konfigurace s uvedenou skupinou, které obsahují výstupy, nemohou mít soubory klíčů. Editory instalačních programů předpokládají, že kanonické názvy a zobrazované názvy skupin a existence souboru klíče se nemění na základě konfigurací.

 Všimněte si, že `IVsOutputGroup` pokud projekt má, že nechce balíček nebo nasazení, stačí neumístit tento výstup do skupiny. Výstup může být stále výčtu normálně <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> implementací metody, která vrací všechny výstupy konfigurace bez ohledu na seskupení.

 Další informace naleznete v `IVsOutputGroup` implementaci v ukázku vlastního projektu na [MPF pro projekty](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="see-also"></a>Viz také
- [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurace projektu pro sestavení](../../extensibility/internals/project-configuration-for-building.md)
- [Objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md)
- [Konfigurace řešení](../../extensibility/internals/solution-configuration.md)
