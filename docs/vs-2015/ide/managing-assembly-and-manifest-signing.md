---
title: Správa sestavení a podepsání manifestu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 831fb08941e16abdb197d3a25e71f2a20fcb14cb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909676"
---
# <a name="managing-assembly-and-manifest-signing"></a>Správa sestavení a podepsání manifestu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podepisování silným názvem poskytuje softwarová součást globálně jedinečné identity. Silné názvy se používají k zajištění, že s falešnou identitou sestavení někým jiným a zajistit závislostí součástí a konfigurace příkazy, které se mapují správné komponenty a verze komponenty.  
  
 Silný název se skládá z identity sestavení (jednoduchý textový název, číslo verze a informace o jazykové verzi), plus token veřejného klíče a digitální podpis.  
  
 Informace o podepisování sestavení v projektech Visual Basic a C# najdete v tématu [vytvoření a použití sestavení](http://msdn.microsoft.com/library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9).  
  
 Informace o podepisování sestavení v projektech Visual C++, naleznete v tématu [sestavení se silným názvem (podepisování sestavení) (C + +/ CLI)](http://msdn.microsoft.com/library/c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc).  
  
## <a name="asset-types-and-signing"></a>Typy prostředků a podepisování  
 Můžete podepisovat manifesty aplikace a sestavení .NET. Patří mezi ně například:  
  
- spustitelné soubory (.exe)  
  
- manifesty aplikací (. exe.manifest)  
  
- manifesty nasazení (.application)  
  
- sdílené komponenty sestavení (.dll)  
  
  Následující typy prostředků, musíte se přihlásit:  
  
1. Sestavení, pokud chcete nasadit do globální mezipaměti sestavení (GAC).  
  
2. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesty aplikace a nasazení. Visual Studio umožňuje podepisování ve výchozím nastavení v případě těchto aplikací.  
  
3. Primární spolupracující sestavení, které se používají pro interoperabilitu COM. Nástroj TLBIMP vynucuje silné názvy při vytváření primárních sestavení vzájemné spolupráce z knihovny typů modelu COM.  
  
   Obecně neměli podepisovat spustitelné soubory. Silný název komponenty nemůže odkazovat na komponenty bez silným názvem, který je nasazen s aplikací. Uživatel spustitelné soubory aplikace Visual Studio, ale místo toho podepíše manifest aplikace, která odkazuje na spustitelný soubor s názvem slabé. Neměli byste obecně, podepisování součásti, které jsou privátní pro vaši aplikaci, protože podepisování může to ztížit Spravovat závislosti.  
  
## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Podepsání sestavení v sadě Visual Studio  
 Podepsání aplikace nebo komponenty pomocí **podepisování** karty v okně Vlastnosti projektu (klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a vyberte **vlastnosti**, nebo typ **vlastnosti projektu** v **Snadné spuštění** okna, nebo stiskněte klávesovou zkratku ALT + ENTER uvnitř **Průzkumníka řešení** okno). Vyberte **podepisování** kartu a potom vyberte **podepsat sestavení** zaškrtávací políčko.  
  
 Zadejte soubor klíče. Pokud budete chtít vytvořit nový soubor klíče, mějte na paměti, že se vždy vytváří nové soubory klíčů ve formátu .pfx. Budete potřebovat jméno a heslo pro nový soubor.  
  
> [!WARNING]
>  Vždy byste měli chránit vašemu souboru s klíčem s heslem někdo zabránit jeho použití. Klíče můžete zabezpečit také pomocí zprostředkovatele nebo úložiště certifikátů.  
  
 Může také odkazovat na klíč, který jste už vytvořili. Další informace o vytváření klíčů najdete v tématu [postupy: vytvoření páru veřejného a privátního klíče](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114).  
  
 Pokud máte přístup pouze k veřejným klíčem, můžete použít zpoždění podepsání odložení přiřazení klíč. Povolit zpoždění podepsání tak, že vyberete **zpoždění podepsání** zaškrtávací políčko. Projekt se zpožděným podpisem se nespustí a nelze ho ladit. Však můžete přeskočit ověření během vývoje s použitím [Sn.exe (nástroj Strong Name)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6) s `-Vr` možnost.  
  
 Informace o podepisování manifestů naleznete v tématu [postupy: přihlášení aplikace a manifesty nasazení](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
## <a name="see-also"></a>Viz také  
 [Sestavení se silným názvem](http://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)   
 [Sestavení se silným názvem (podepisování sestavení) (C++/CLI)](http://msdn.microsoft.com/library/c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc)



