<mxfile host="app.diagrams.net">
  <diagram name="Arquitetura TDM Final">
    <mxGraphModel dx="1600" dy="900" grid="1" gridSize="10">
      <root>
        <mxCell id="0"/>
        <mxCell id="1" parent="0"/>

        <!-- TSYS FILES -->
        <mxCell id="2" value="TSYS&#xa;Files (Batch)" style="shape=folder;fillColor=#dae8fc;" vertex="1" parent="1">
          <mxGeometry x="40" y="100" width="160" height="80" as="geometry"/>
        </mxCell>

        <!-- TSYS API -->
        <mxCell id="3" value="TSYS APIs&#xa;(Criação de Massa)" style="shape=cloud;fillColor=#dae8fc;" vertex="1" parent="1">
          <mxGeometry x="900" y="280" width="220" height="100" as="geometry"/>
        </mxCell>

        <!-- ETL -->
        <mxCell id="4" value="ETL Python&#xa;Parsing + Normalização" style="shape=process;fillColor=#fff2cc;" vertex="1" parent="1">
          <mxGeometry x="240" y="100" width="220" height="90" as="geometry"/>
        </mxCell>

        <!-- DATABASE -->
        <mxCell id="5" value="Base de Massas (TDM)&#xa;Estado + Histórico" style="shape=cylinder;fillColor=#e1d5e7;" vertex="1" parent="1">
          <mxGeometry x="520" y="90" width="240" height="110" as="geometry"/>
        </mxCell>

        <!-- WORKERS -->
        <mxCell id="6" value="Maturação (Workers)&#xa;LDSG + Regras" style="shape=process;fillColor=#d5e8d4;" vertex="1" parent="1">
          <mxGeometry x="800" y="80" width="260" height="110" as="geometry"/>
        </mxCell>

        <!-- API -->
        <mxCell id="7" value="API de Massas&#xa;CRUD + Orquestração" style="rounded=1;fillColor=#f8cecc;" vertex="1" parent="1">
          <mxGeometry x="520" y="280" width="240" height="90" as="geometry"/>
        </mxCell>

        <!-- QA -->
        <mxCell id="8" value="QA / Automação" style="shape=actor;" vertex="1" parent="1">
          <mxGeometry x="240" y="280" width="60" height="100" as="geometry"/>
        </mxCell>

        <!-- FLOWS -->
        <mxCell id="9" edge="1" source="2" target="4" style="endArrow=block;" parent="1">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="10" edge="1" source="4" target="5" style="endArrow=block;" parent="1">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="11" edge="1" source="5" target="6" style="endArrow=block;dashed=1;" parent="1">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="12" edge="1" source="6" target="5" style="endArrow=block;dashed=1;" parent="1">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="13" edge="1" source="7" target="5" style="endArrow=block;" parent="1">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="14" edge="1" source="8" target="7" style="endArrow=block;" parent="1">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <!-- CRIAÇÃO DE MASSA -->
        <mxCell id="15" edge="1" source="7" target="3" style="endArrow=block;" parent="1">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="16" edge="1" source="3" target="5" style="endArrow=block;" parent="1">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

      </root>
    </mxGraphModel>
  </diagram>
</mxfile>