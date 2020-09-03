---
title: JavaScript
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-javascript
ms.topic: conceptual
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 778912c3149f9f146c01dbab15afa4fabeaa49b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852262"
---
# <a name="javascript-in-visual-studio"></a>JavaScript ve Visual Studiu 2012
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript je první třídou jazyka v aplikaci Visual Studio. Při psaní kódu v jazyce JavaScript v sadě Visual Studio IDE můžete použít téměř všechny standardní editační pomůcky (fragmenty kódu, funkci IntelliSense atd.). Můžete psát kód JavaScriptu pro mnoho typů aplikací a služeb.

 Referenční dokumentaci jazyka JavaScript naleznete v tématu [JavaScript](https://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).

 Konkrétní verze aplikace Visual Studio nebo specifická rozšíření sady Visual Studio mohou být požadovány pro vývoj určitých typů a služeb aplikací pomocí jazyka HTML a JavaScriptu. Následující seznam obsahuje odkazy na Další informace.

- Pokud chcete vytvářet aplikace pro různé platformy pomocí Apache Cordova, [získejte Visual Studio Tools pro Apache Cordova](https://taco.visualstudio.com/docs/install-vs-tools-apache-cordova/).

- Pokud chcete vytvořit [Windows Store](https://developer.microsoft.com/), [Windows Phone](https://developer.microsoft.com/)a univerzální aplikace (podporující obě platformy), [Získejte nástroje](https://developer.microsoft.com/windows/downloads).

- Chcete-li vytvořit cloudové služby, přečtěte si [web Microsoft Azure](https://azure.microsoft.com/documentation/).

- Informace o vytváření webů a webových aplikací [najdete na webu ASP.NET](https://dotnet.microsoft.com/apps/aspnet/web-apps).

  > [!NOTE]
  > Můžete vytvořit prázdný web ASP.Net a použít ho pro programování ve formátu HTML, CSS a JavaScript. Soubor WebConfig, který poskytuje ASP.NET, umožňuje ladění v aplikaci Visual Studio (nebo můžete použít nástroje F12 při spuštění aplikace).

  Editor jazyka JavaScript v aplikaci Visual Studio poskytuje podporu technologie IntelliSense. Další informace naleznete v tématu [JavaScript IntelliSense](../ide/javascript-intellisense.md).

## <a name="whats-new-in-javascript"></a>Co je nového v jazyce JavaScript
 Nové funkce pro JavaScript jsou uvedené v následující tabulce.

|Funkce|Popis|
|-------------|-----------------|
|Třídy|Nová syntaxe podporuje deklaraci [tříd](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/class).|
|Příslibů|[Příslibů](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) umožňuje snadnější a čisticí asynchronní kódování. Jsou podporovány konstruktory příslib spolu s `all` `race` metodami a.|
|Iterátory|Nyní můžete iterovat objekty iterující (včetně polí, objektů podobných poli a iterátory), a to voláním vlastního iteračního zavěšení s příkazy, které mají být provedeny, pro hodnotu každé vlastnosti DISTINCT. Další informace najdete v tématu [iterátory a generátory](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Iterators_and_Generators). **Poznámka:**  Generátory ještě nejsou podporované.|
|Šipky – funkce|Funkce šipky (=>) poskytuje zkrácený Syntax pro `function` klíčové slovo, které obsahuje lexikální `this` vazbu.|
|Nové metody pro předdefinované objekty|Objekty [pole](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array), [objekt Math Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Math), [číslo objektu](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number), [objekt objektu](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)a objekty [řetězce](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String) v předdefinovaných objektech obsahují mnoho nových funkcí nástrojů a vlastnosti pro manipulaci a kontrolu dat.|
|Vylepšení literálu objektu|Objekty nyní podporují vypočítané vlastnosti, stručné definice metod a zkrácený Syntax pro vlastnosti, jejichž hodnota je inicializována na stejnou proměnnou s názvem. Další informace najdete v tématu [vytváření objektů](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object).|
|Proxy|[Proxy](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Proxy) umožňují vlastní chování objektů.|
|Parametry REST|Parametry REST umožňují ve volání funkce do pole přepínat po sobě jdoucí argumenty. Další informace najdete v tématu [funkce](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function).|
|Operátor rozprostření|[Operátor rozprostření](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Spread_operator) ( `…` ) rozbalí výrazy iterující do jednotlivých argumentů. Například `a.b(…array)` je přibližně stejný jako `a.b.apply(a, array)` .|
|Symboly|Objekty [symbolů](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Symbol) umožňují přidání vlastností do existujících objektů bez možnosti rušivého narušování s existujícími vlastnostmi objektu bez nezamýšlené viditelnosti a bez dalších nekoordinujících dodatků jiným kódem.|
|Řetězce šablon|[Řetězce šablon](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Template_literals) jsou řetězcové literály, které umožňují vyhodnotit výrazy a zřetězit je pomocí řetězcového literálu.|
|Vylepšení kódování Unicode|Byla provedena vylepšení podpory kódování Unicode. Například nový formát řídicí sekvence podporuje body kódu Astral (body kódu s více než čtyřmi šestnáctkovými číslicemi). Další informace najdete v tématu [speciální znaky](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Regular_Expressions#Types_of_special_characters).|
|WeakSet|[Weakset](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/WeakSet) je kolekce objektů, které budou uvolněny z paměti, pokud neodkazují kamkoli jinde.|
