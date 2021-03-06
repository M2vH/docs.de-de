---
title: Objektverweise
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a86b442ffeeeb77a0c124b9b3e3441ba24d68e4a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="object-references"></a>Objektverweise
In diesem Beispiel wird veranschaulicht, wie Objekte als Verweis zwischen Server und Client übergeben werden. Das Beispiel verwendet simuliert *sozialen Netzwerken*. Ein gesellschaftliches Netzwerk besteht aus einer `Person`-Klasse, die eine Liste von Freunden enthält, wobei jeder Freund eine Instanz der `Person`-Klasse mit eigener Liste von Freunden ist. Damit wird ein Objektdiagramm erstellt. Der Dienst macht Operationen in diesen gesellschaftlichen Netzwerken verfügbar.  
  
 In diesem Beispiel wird der Dienst von Internetinformationsdiensten (IIS) gehostet, und der Client ist eine Konsolenanwendung (.exe).  
  
> [!NOTE]
>  Die Setupprozedur und die Buildanweisungen für dieses Beispiel befinden sich am Ende dieses Themas.  
  
## <a name="service"></a>Dienst  
 Auf die `Person`-Klasse wurde das <xref:System.Runtime.Serialization.DataContractAttribute>-Attribut angewendet, wobei das <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>-Feld zur Deklaration als Verweistyp auf `true` festgelegt wurde. Auf alle Eigenschaften wurde das <xref:System.Runtime.Serialization.DataMemberAttribute>-Attribut angewendet.  
  
```  
[DataContract(IsReference=true)]  
public class Person  
{  
    string name;  
    string location;  
    string gender;  
    int age;  
    List<Person> friends;  
    [DataMember()]  
    public string Name  
    {  
        get { return name; }  
        set { name = value; }  
    }  
    [DataMember()]  
    public string Location  
    {  
        get { return location; }  
        set { location = value; }  
    }  
    [DataMember()]  
    public string Gender  
    {  
        get { return gender; }  
        set { gender = value; }  
    }  
…  
}  
```  
  
 Der `GetPeopleInNetwork`-Vorgang akzeptiert einen Parameter vom Typ `Person` und gibt alle Personen im Netzwerk; d. h. alle Personen in der `friends`-Liste, die Freunde des Freundes usw. ohne Duplikate zurück.  
  
```  
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 Der `GetMutualFriends`-Vorgang akzeptiert einen Parameter vom Typ `Person` und gibt alle Freunde in der Liste zurück, die diese Person ebenfalls in ihrer `friends`-Liste haben.  
  
```  
public List<Person> GetMutualFriends(Person p)  
{  
    List<Person> mutual = new List<Person>();  
    foreach (Person friend in p.Friends)  
    {  
        if (friend.Friends.Contains(p))  
            mutual.Add(friend);  
    }  
    return mutual;  
}  
```  
  
 Der `GetCommonFriends`-Vorgang akzeptiert eine Liste vom Typ `Person`. Es wird erwartet, dass die Liste zwei `Person`-Objekte enthält. Der Vorgang gibt eine Liste von `Person`-Objekten zurück, die in den `friends`-Listen beider `Person`-Objekte in der Eingabeliste enthalten sind.  
  
```  
public List<Person> GetCommonFriends(List<Person> people)  
{  
    List<Person> common = new List<Person>();  
    foreach (Person friend in people[0].Friends)  
        if (people[1].Friends.Contains(friend))  
            common.Add(friend);  
    return common;  
}  
```  
  
## <a name="client"></a>Client  
 Der Clientproxy wird erstellt, mit der **Hinzufügen eines Dienstverweises** Feature von [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].  
  
 Ein gesellschaftliches Netzwerk wird erstellt, das aus fünf `Person`-Objekten besteht. Der Client ruft jede der drei Methoden im Dienst auf.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>So können Sie das Beispiel einrichten, erstellen und ausführen  
  
1.  Stellen Sie sicher, dass Sie ausgeführt haben die [Setupprozedur für die Windows Communication Foundation-Beispiele zum einmaligen](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Um die C#- oder Visual Basic .NET-Edition der Projektmappe zu erstellen, befolgen Sie die unter [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)aufgeführten Anweisungen.  
  
3.  Um das Beispiel in einer einzelnen oder computerübergreifenden Konfiguration ausführen möchten, folgen Sie den Anweisungen [Ausführen der Windows Communication Foundation-Beispiele](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Die Beispiele sind möglicherweise bereits auf dem Computer installiert. Suchen Sie nach dem folgenden Verzeichnis (Standardverzeichnis), bevor Sie fortfahren.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Wenn dieses Verzeichnis nicht vorhanden ist, rufen Sie [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) auf, um alle [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] - und [!INCLUDE[wf1](../../../../includes/wf1-md.md)] -Beispiele herunterzuladen. Dieses Beispiel befindet sich im folgenden Verzeichnis.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>  
 [Interoperable Objektverweise](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
