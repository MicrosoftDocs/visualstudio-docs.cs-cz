---
title: Konfigurace pro výstup projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1c23f9210175b848bfdf3ddab56776092e39212c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51740892"
---
# <a name="project-configuration-for-output"></a>Konfigurace projektu pro výstup
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Všechny konfigurace může podporovat sadu procesy sestavení, které se vytvoří výstupní položky, jako jsou soubory spustitelný soubor nebo prostředek. Tyto položky výstupu jsou privátní pro uživatele a mohou být umístěny ve skupinách, které jsou propojeny související typy výstupu, jako je například spustitelné soubory (.exe, .dll, LIB) a zdrojových souborů (.idl, souborů .h).  
  
 Výstupní položky může být k dispozici prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> metody a výčtu s <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> metody. Pokud chcete skupinu výstupní položky projektu by měly také implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> rozhraní.  
  
 Konstrukce vypracovanou organizací cccppf implementace `IVsOutputGroup` umožňuje projekty do výstupů skupiny podle využití. Například knihovny DLL mohou být seskupeny s jeho databázi programu (PDB).  
  
> [!NOTE]
>  Soubor PDB obsahuje informace o ladění a je vytvořen, pokud je zadán parametr "Generovat ladicí informace při sestavování .dll nebo .exe. Soubor PDB se obvykle generuje pro ladění pouze v konfiguraci projektu.  
  
 Projekt musí vracet stejný počet skupin pro každou konfiguraci, která ho podporuje, i když počet výstupů obsažena ve skupině, které se mohou lišit od konfigurace. Například Matt v projektu knihovny DLL může zahrnovat mattd.dll a mattd.pdb v konfiguraci ladění, ale pouze matt.dll v prodejní konfiguraci.  
  
 Skupiny také mít stejný identifikátor informace, například kanonický název, zobrazovaný název a informace o skupině z konfigurace v rámci projektu. Taková konzistence umožňuje nasazení a balení i nadále fungovat i v případě, že změna konfigurace.  
  
 Skupiny můžete taky nechat klíče výstup, který umožňuje zkratky balení tak, aby odkazoval na něco smysluplného. Žádné skupiny může být prázdná v příslušné konfiguraci, tak žádné předpoklady, třeba o velikosti skupiny. Velikost (počet výstupů) v jakékoli konfiguraci každé skupiny se může lišit od velikosti jinou skupinu do stejné konfigurace. Může být také liší od velikost do stejné skupiny v jiné konfigurace.  
  
 ![Obrázek skupiny výstupu](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
Skupiny výstupu  
  
 Primární použití <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> rozhraní je poskytnutí přístupu k vytvoření, nasazení a ladění objekty sady management a projekty povolit volného skupiny výstupy. Další informace o použití tohoto rozhraní najdete v tématu [objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md).  
  
 Na předchozím obrázku, vytvořené skupiny má klíč výstup napříč konfiguracemi (bD.exe nebo b.exe) proto uživatel může vytvořit zástupce pro předdefinované a vědět, že zástupce bude fungovat bez ohledu na konfiguraci nasazení. Zdroj skupiny nemá klíč výstupu, takže uživatel nemůže vytvořit zástupce. Pokud ladění skupiny vytvořené má klíče výstup, ale prodejní skupina vytvořena tak není, který bude nesprávná implementace. Postupuje, potom, pokud žádnou konfiguraci má skupinu, která obsahuje žádné výstupy, a proto není soubor klíče a další konfigurace pomocí této skupiny, které obsahují výstupy nemůže mít soubory klíčů. Editory instalační program předpokládat, že kanonické názvy a zobrazované názvy skupin a navíc existence souboru klíče, neměňte závislosti v konfiguracích.  
  
 Všimněte si, že pokud projekt obsahuje `IVsOutputGroup` , nechce balíček nebo nasazení, stačí tento výstup není umístit do skupiny. Ve výstupu mohou být stále obvykle uvedené implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> metodu, která vrátí všechny výstupy konfigurace bez ohledu na to seskupení.  
  
 Další informace najdete v tématu provádění `IVsOutputGroup` v ukázce projektu vlastní na [MPF projektů](http://mpfproj12.codeplex.com).  
  
## <a name="see-also"></a>Viz také  
 [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)   
 [Konfigurace projektu pro sestavení](../../extensibility/internals/project-configuration-for-building.md)   
 [Objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md)   
 [Konfigurace řešení](../../extensibility/internals/solution-configuration.md)

