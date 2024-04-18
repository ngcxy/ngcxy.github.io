---
layout: page
title: 'Trojan Map'
description: a C++ Map&Navigation Application
img: assets/img/6/short.png
importance: 45
category:
giscus_comments: true
---

This project focuses on using data structures in C++ and implementing various graph algorithms to build a map application.

Code Link on [GitHub](https://github.com/ngcxy/TrojanMap)

Video Presentation on [YouTube](https://www.youtube.com/watch?v=dTmSdIphrBw)

Find details about this course project in [README](https://github.com/ngcxy/TrojanMap/blob/main/README.md) and [REPORT](https://github.com/ngcxy/TrojanMap/blob/main/REPORT.md) file


### Algorithm Highlights

---

```c++
int CalculateEditDistance(std::string name1, std::string name2)
```
- Dynamic Programming

---

```c++
std::vector<std::string> CalculateShortestPath_Dijkstra(std::string &location1_name, std::string &location2_name)
std::vector<std::string> CalculateShortestPath_Bellman_Ford(std::string &location1_name, std::string &location2_name)
```
- Dijkstra & Bellman Ford

Example

```shell
**************************************************************
* 6. CalculateShortestPath                                    
**************************************************************

Please input the start location:Ralphs
Please input the destination:Target
*************************Dijkstra*****************************
*************************Results******************************
"2578244375","4380040154","4380040158","4380040167","6805802087","8410938469","6813416131","7645318201","6813416130","6813416129","123318563","452688940","6816193777","123408705","6816193774","452688933","452688931","123230412","6816193770","6787470576","4015442011","6816193692","6816193693","6816193694","4015377691","544693739","6816193696","6804883323","6807937309","6807937306","6816193698","4015377690","4015377689","122814447","6813416159","6813405266","4015372488","4015372487","6813405229","122719216","6813405232","4015372486","7071032399","4015372485","6813379479","6813379584","6814769289","5237417650",
The distance of the path is:0.927969 miles
**************************************************************
Time taken by function: 39 ms

*************************Bellman_Ford*************************
*************************Results******************************
"2578244375","4380040154","4380040158","4380040167","6805802087","8410938469","6813416131","7645318201","6813416130","6813416129","123318563","452688940","6816193777","123408705","6816193774","452688933","452688931","123230412","6816193770","6787470576","4015442011","6816193692","6816193693","6816193694","4015377691","544693739","6816193696","6804883323","6807937309","6807937306","6816193698","4015377690","4015377689","122814447","6813416159","6813405266","4015372488","4015372487","6813405229","122719216","6813405232","4015372486","7071032399","4015372485","6813379479","6813379584","6814769289","5237417650",
The distance of the path is:0.927969 miles
**************************************************************
Time taken by function: 7084 ms
```

---

```c++
bool CycleDetection(std::vector<double> &square)
```
- DFS to detect cycle

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/6/cycle.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

---

Traveling Salesman

```c++
std::pair<double, std::vector<std::vector<std::string>>> TravelingTrojan_Brute_force(std::vector<std::string> location_ids)
```

```c++
std::pair<double, std::vector<std::vector<std::string>>> TravelingTrojan_Backtracking(std::vector<std::string> location_ids)
```

```c++
std::pair<double, std::vector<std::vector<std::string>>> TravelingTrojan_2opt(std::vector<std::string> location_ids)
```

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/6/output.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
