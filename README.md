import pymssql

def conexao_bd_sql(self):
    try:
        conn = pymssql.connect(
            server='AGSQLINFRAH.csfcpv.wcorp.carrefour.com',
            port=32332,
            user='svc_massa_tdm',
            password='svc_massa_tdm',
            database='DbTdm'
        )

        cursor = conn.cursor()
        return cursor

    except Exception as exception_error:
        raise Exception(
            '[ERRO] Não foi possível realizar a conexão ou ação com o banco de dados.\n'
            'Detalhes do erro: {}'.format(exception_error)
        )


def conexao_bd_sql_cert(self):
    try:
        conn = pymssql.connect(
            server='AGSQLINFRAH.csfcpv.wcorp.carrefour.com',
            port=32332,
            user='platre',   # ajuste se necessário
            password='platre'
            # ⚠️ aqui você NÃO colocou database no original, então mantive igual
        )

        cursor = conn.cursor()
        return cursor

    except Exception as exception_error:
        raise Exception(
            '[ERRO] Não foi possível realizar a conexão ou ação com o banco de dados.\n'
            'Detalhes do erro: {}'.format(exception_error)
        )