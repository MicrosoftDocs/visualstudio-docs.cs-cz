---
title: Konfigurace projektu pro výstup | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: addd7e8630ce35c6bdbbbb4c063197f75a74c97d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300681"
---
# <a name="project-configuration-for-output"></a>Konfigurace projektu pro výstup
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Každá konfigurace může podporovat sadu procesů sestavení, které vytvářejí výstupní položky, jako jsou spustitelné soubory nebo soubory prostředků. Tyto výstupní položky jsou pro uživatele soukromé a lze je umístit do skupin, které odkazují na související typy výstupu, jako jsou spustitelné soubory (. exe,. dll,. lib) a zdrojové soubory (. idl,. h soubory).  
  
 Výstupní položky mohou být zpřístupněny prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> metody a výčty s metodami <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>. Pokud chcete seskupit výstupní položky, váš projekt by měl také implementovat rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>.  
  
 Konstrukce vyvinutá implementací `IVsOutputGroup` umožňuje projektům seskupovat výstupy podle využití. Například knihovna DLL může být seskupena s jeho programovou databází (PDB).  
  
> [!NOTE]
> Soubor PDB obsahuje ladicí informace a je vytvořen při zadání možnosti generovat informace o ladění při vytváření souboru. dll nebo. exe. Soubor. pdb je obvykle generován pouze pro ladění konfigurace projektu.  
  
 Projekt musí vracet stejný počet skupin pro každou konfiguraci, kterou podporuje, a to i v případě, že se počet výstupů obsažených v rámci skupiny může lišit od konfigurace až po konfiguraci. Například knihovna DLL podkladu projektu může zahrnovat podkladové knihovny DLL a podkladové soubory. pdb v konfiguraci ladění, ale do konfigurace maloobchodního prodeje zahrnout pouze podklady. dll.  
  
 Skupiny mají také stejné informace o identifikátoru, jako je kanonický název, zobrazovaný název a informace o skupině, od konfigurace po konfiguraci v rámci projektu. Tato konzistence umožňuje nasazení a balení i v případě změny konfigurace.  
  
 Skupiny mohou mít také výstup klíče, který umožňuje, aby zástupci balení odkazovali na něco smysluplného. Libovolná skupina může být v dané konfiguraci prázdná, takže nemusíte mít k dispozici žádné předpoklady o velikosti skupiny. Velikost (počet výstupů) každé skupiny v libovolné konfiguraci může být jiná než velikost jiné skupiny ve stejné konfiguraci. Může se také lišit od velikosti stejné skupiny v jiné konfiguraci.  
  
 ![Grafika výstupních skupin](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
Skupiny výstupu  
  
 Primární použití rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> slouží k poskytnutí přístupu k sestavování, nasazování a ladění objektů správy a umožňuje projektům, aby bylo možné seskupovat výstupy. Další informace o použití tohoto rozhraní naleznete v tématu [objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md).  
  
 V předchozím diagramu má skupina sestavený výstup v různých konfiguracích (bD. exe nebo b. exe), takže uživatel může vytvořit zástupce, který se vytvoří a zjistí, že zástupce bude fungovat bez ohledu na nasazenou konfiguraci. Zdroj skupiny nemá výstup klíče, takže uživatel nemůže pro něj vytvořit zástupce. Pokud má skupina ladění sestavený výstup klíče, ale maloobchodní skupina sestavena nemá, jedná se o nesprávnou implementaci. Následuje, to znamená, že pokud má kterákoli z konfigurací skupinu, která neobsahuje žádné výstupy, a v důsledku toho nebude mít žádný soubor klíče ani jiné konfigurace s touto skupinou, které obsahují výstupy, soubory klíčů. Editory instalačního programu předpokládají, že kanonické názvy a zobrazované názvy skupin a také existenci souboru klíče se nemění v závislosti na konfiguracích.  
  
 Všimněte si, že pokud má projekt `IVsOutputGroup`, že nechce zabalit nebo nasadit, stačí tento výstup vložit do skupiny. Výstup může být v normálním výčtu, protože implementuje metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A>, která vrátí všechny výstupy konfigurace bez ohledu na seskupení.  
  
 Další informace naleznete v tématu Implementace `IVsOutputGroup` v ukázce vlastního projektu v souboru [MPF pro projekty](https://archive.codeplex.com/?p=mpfproj12).  
  
## <a name="see-also"></a>Viz také  
 [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)   
 [Konfigurace projektu pro vytváření](../../extensibility/internals/project-configuration-for-building.md)   
   [objekt konfigurace projektu](../../extensibility/internals/project-configuration-object.md)  
 [Konfigurace řešení](../../extensibility/internals/solution-configuration.md)
